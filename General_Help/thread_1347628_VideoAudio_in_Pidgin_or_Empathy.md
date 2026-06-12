---
title: "Video/Audio in Pidgin or Empathy"
date: 2009-12-06
forum: General Help
---

### Post by jeremz on 2009-12-06
Does anyone have this working? I can't for the life of me get a simple audio chat with my wife across the room going using the google talk protocol with either Pidgin or Empathy. We can call each other, but not transmit audio or video. I called her from fring on my Android phone, and she could hear me, so I think we just aren't transmitting from Ubuntu. I can't find any way to configure the audio or video sources in the gui. Any thoughts?

---

### Post by jesse0 on 2009-12-23
It works for me with Empathy. You have to have your account configured as a Gtalk account, not a Jabber account which is what mine was configured as.

---

### Post by giorx on 2009-12-29
I think this link could be helpful
[http://alsuren.wordpress.com/2009/10/09/telepathic-reverberations/](http://alsuren.wordpress.com/2009/10/09/telepathic-reverberations/)

"...Users of the Google Mail interface are currently limited to audio only, because Google only uses the h.264 video codec, which cannot legally be distributed with Empathy. If enough people report this problem to them, then maybe they will include Theora as a fallback. There are ways that I could work around this problem for the echo service, but then it wouldn’t be a very good tool for testing whether you’re capable of calling Empathy users".

---

### Post by giorx on 2010-01-04
It works also for me, you just need to install h264 codec.
See the FAQ: [http://live.gnome.org/Empathy/FAQ](http://live.gnome.org/Empathy/FAQ)

---

### Post by segalion on 2010-03-02
All this conference programs usually dont work if all peers are behind same NAT IP address. You have to test first with other internet location.

---

### Post by gradinaruvasile on 2010-03-02
> **segalion said:**
> All this conference programs usually dont work if all peers are behind same NAT IP address. You have to test first with other internet location.

Testing is common sense, but these programs work via the jabber protocol (GTalk included) and that works fine (i tested Pidgin audio/video via VPNs and worked just fine). Its not the SIP protocol, that indeed has NAT traversal issues.

I'd say use Pidgin of these 2. Empathy is a great idea, but the implementation is lacking quality. It has tons of components that sometimes dont work as expected (i had various issues with mission control running after exiting and such). And the configuration options are overly simplified and lacking.

Pidgin on the other hand is a more complete and polished program and has more comprehensive configuration options. And it has the habit of working as expected. I say this after using both Empathy and Pidgin for a long time. 

Tip for the Pidgin video plugin configuration: set the video device explicitly on both ends - if there is no camera, set it to "Test input", otherwise it might not work.

---

### Post by KEE on 2010-04-12
> **gradinaruvasile said:**
> 

Tip for the Pidgin video plugin configuration: set the video device explicitly on both ends - if there is no camera, set it to "Test input", otherwise it might not work.

explain the steps please its not like ubuntu has a device manager =S what app did you use?

---

### Post by KEE on 2010-04-12
> **KEE said:**
> explain the steps please its not like ubuntu has a device manager =S what app did you use?

nevermind its in pidgin

---

### Post by fonsi2099 on 2010-04-14
Help ...I've have no video possibility to my MSN contacts, any idea? Thank you.

---

