---
layout: page
title: Removed Content
---

# This content has been temporarily removed, and will be restored (and rewritten) later

Intended for keeping anything not ready to go in the report yet.

### To do:

**Encryption:**
- DH algorithm
- WebRTC previously used SDES
    - Encryption key is embedded in header
    - Anybody could read the key

**Look at SIP book**

http://www.kapejod.org/en/2014/05/security-implications-of-webrtc-part-2-end-to-end-encryption-well-no/
-> Use for "Coding best-practices!"
-> Also - STUN gun?

**Redraw diagrams etc**

### WebRTC-specific areas of interest: (Checklist)

- Identity Management ✔︎
- Browser Security
- Authentication
- Media encryption ✔︎

### Other Stuff

Information that doesn't yet have a place, or was moved. For future consideration.

WebRTC's powerful APIs allow developers to develop real-time communications applications in the browser without the need for any downloads or plugins to run.
- The proliferation of media streaming applications also presents new considerations within the realm of security.
- WebRTC bypasses this by offering developers end-to-end encryption by default in their applications
    - Developers can easily reassure their users


*Can I use WebRTC to open a UDP connection?*

No. There are too many security issues allowing WebRTC to send to a random address/port - we have to make sure it doesn't work as a DDOS platform, so we require the target to implement ICE as an implicit permission to send data, and we also don't allow sending arbitrary data, just SRTP mediastreams and data in DataChannels (over SCTP over DTLS over UDP+ICE).


*Encryption*

WebRTC employs mandatory encryption for both media and data.

- Secure pathways
    - Signaling is secured by using HTTPS
    - Media/Data communications are encrypted using different technologies:
      - Audio/Video data is sent other SRTP
      - Data is sent over DTLS

Encrypted Communications is undoubtably the most important security aspect for WebRTC. Due to the security guarentees offered by this protection, any connected peers know that their communications are both

"security guarentees provided by..." <- let's use this somewhere else! Sounds good.

Additional coding practice:

2. Make sure that ICE values are masked thereby not rendering the caller/ callee’s IP and location to each other through tracing in chrome://webrtc-internals/ or packet detection in Wirehsark on user’s end.

Further to the above, WebRTC components run in a sandbox within the browser and not in a separate process. (Installation & updates)


**Access to Media/Local resources (Part 2)**

- Web servers are strictly limited or forbidden from accessing local files, camera and microphone.

- Possible to produce an HTML form which will allows file upload...
    - But a script cannot do it without user consent
    - And cannot specify a particular file! (e.g. /etc/passwd)
        - User explicitly selects file and agrees to uploading

        - Browsers are often explicitly designed to avoid dialogs with the semantics of "click here to screw yourself!"



Similarly, we cannot allow web servers to arbitrarily initiate calls or otherwise access a user's microphone or webcam.
If no access restrictions were enforced, a site could spy upon a user without prior given user consent.

These mechanisms enforce that the user has control over which applications are permitted access to their media, and that they are visually reminded that such activity is occurring. Even if the user were to forget they had permitted an app to broadcast from their media devices, the browser UI will remind them such that they can disable the app before accidentally broadcasting unintended behaviour or information.
-> Perhaps not implemented yet

DTLS-SRTP
- Ensures that any MITM attack can be detected (Incorporate Iwase-san's comment here.) (https://support.silentcircle.com/customer/portal/articles/1644771-what-about-dtls-srtp-why-not-use-that-)

- Registration hijacking
 - Allows attacker to cut off calls that are about to come and conclude how those calls are routed.

#### Attacks on DTLS

http://www.isg.rhul.ac.uk/~kp/dtls.pdf
- Heartbleed



## 4.7 (???) RTC Security Considerations


**Security in RTC Apps**

#### VoIP attacks

**Leave in or remove?**

As an upcoming VoIP technology, there is naturally the risk that WebRTC may inherit some traditional VoIP attacks. In this section we will examine such concerns.

Denial of Service attacks (DoS attacks) rely on the delivery of massive quantities of messages (signalling traffic) in order to exhaust the CPU, memory or bandwidth of the target system or device. One possible motive could be to obtain login, password or extension number info. Or else, an attack could also be used to force a crash in a SIP proxy.

Traditional VoIP attacks normally involved network attackers.
- With WebRTC we also need to deal with web attackers. WebRTC services must be designed to protect against both.



### 6.1. Case Studies

*To be discussed with team*

Part of above topic?

Idea:

- Make multi-party conference app
    - With weaknesses?
    - Explain how to resolve weaknesses.
    
    
    
**Other areas of Security risk:**

- Improperly coded applications/Incorrectly implemented protocols
    - Are such applications at risk?
    - Not likely, no.

- Operating System bugs

- Social engineering and phishing attacks
    - Research this.

- Identity Management


(From conclusion)

It is not feasible to send unencrypted media using a WebRTC application. The WebRTC specification forbids the transmission of media streams over unencrypted RTP. (Specifically, it is forbidden that implementations negotiate cipher suits with NULL encryption modes.) (See: https://tools.ietf.org/html/draft-ietf-rtcweb-security-arch-11#section-5.5)

This ensures users are protected from unwanted intrusions into their private communication, and maintains information integrity by disallowing information tampering on data channels. With appropriate encryption, it is infeasible for a malicious third party to eavesdrop on the encrypted contents. The (correct) secret key is necessary to decrypt the ciphertext. Without the key, the third party will only be able to see seemingly random (meaningless) data.

- Flash
- Silverlight
- Jabber
- Skype
- SIP

Although widely relied upon, the additional installation process for most technologies can pose it's own barrier for adoption. 