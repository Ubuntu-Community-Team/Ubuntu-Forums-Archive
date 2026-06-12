---
title: "please help with gizmo5 and google voice"
date: 2009-11-13
forum: General Help
---

### Post by ngage on 2009-11-13
What works and doesn't work when using google voice + gizmo5 since the aquisition:

1. SUCCESS: Signed in to google voice and successfully added my gizmo number and verified it with google voice by entering two-digit handshake code when answering the call through gizmocall.com

2. SUCCESS: Free call in does work.  When someone calls my google voice number, the call is free.

3. SUCCESS: Free call out works by initiating the call from google voice. since google voice calls your sip number, the call out is actually a call in and is free.

4. PROBLEM: Attempted to call out through gizmo5.  Gizmo5 offers 3 free minutes calling through google voice.  When i called my friend's number, i got the operator telling me to purchase call out minutes.

5.  PROBLEM: Attempted to call out, this time calling my google voice number.  Got the same must purchase call out minutes message.

Note: every google voice tutorial like this [http://www.jrin.net/2009_07_26/use-gizmo5-for-free-calls-with-google-voice](http://www.jrin.net/2009_07_26/use-gizmo5-for-free-calls-with-google-voice) seems to indicate that there should be some dialog box at my.gizmo5.com account page where you enter your google voice number (SEE ATTACHMENT).  But the page appears to have changed since google bought gizmo5, and there does not appear to be anywhere to input my google voice number.  Perhaps this is related to the call out problem.

I would actually be happy paying for the call out minutes if i could verify that the service works.  Obviously, this service is extremely important for ubuntu users like myself.  i would even like to use this with my nokia n800 (maemo linux which ubuntu mobile is based on) in addition to my ubuntu laptop.

---

### Post by mdonahoe on 2009-11-23
In Google Voice make sure you have added the Gizmo number then set phone type to be Gizmo5.  On the Gizmo5 side make sure under the Call IN you have set it to Accept all calls.  From the sound of things you are trying to forward a call (call out) which requires your call out to be funded, just like skype.

---

### Post by JohnGalt on 2009-12-06
Have you had any luck? Apparently Google has taken the linux app out of their pages. I managed to get it downloaded. I can make a call out, and can receive calls, but it doesn't ever ring unfortunately. I'm trying twinkle but the interface is horrible and doesn't seem to be ringing in either.

To set up both I just put in my username and password and placed the call to a land line with no problem.

---

### Post by ngage on 2009-12-20
john,

i use ekiga with with gizmo5/google voice and it doesn't ring when a call comes in either.  however, i am able to receive calls.  when a call comes in, a notation box comes up allowing me to accept the call.  i see ekiga's call-in .wav file and when i play it in mplayer it plays fine but it just doesn't ring when a call comes in.  weird. anyway, you might want to try ekiga.  it is actively worked on and seems to improve quite a bit with each new release.  

it's too bad that ubuntu dropped ekiga, but a ppa is actively maintained so it's no problem to install:
[https://launchpad.net/~sevmek/+archive/ekiga-released](https://launchpad.net/~sevmek/+archive/ekiga-released)

---

