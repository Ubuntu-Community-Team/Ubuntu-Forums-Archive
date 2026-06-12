---
title: "You Tube video downloads"
date: 2009-09-04
forum: General Help
---

### Post by Vinu Raj V on 2009-09-04
Which application is prefered for downloading videos from You Tube? Are community maintained software's available?

---

### Post by Vaphell on 2009-09-04
i have bookmark which does just that in FF

javascript:if(document.location.href.match(/http:\/\/[a-zA-Z\.]*youtube\.com\/watch/)){document.location.href='http://www.youtube.com/get_video?fmt='+(isHDAvailable?'22':'18')+'&video_id='+swfArgs['video_id']+'&t='+swfArgs['t']}

besides you can look for the flash file in /tmp directory

---

### Post by HermanAB on 2009-09-04
The easiest way is to play the video using a web browser and then look for the file in the /tmp directory.  The /tmp is cleaned on each reboot. Lots of useful stuff end up there for a while.

---

### Post by gordintoronto on 2009-09-04
> **Vinu Raj V said:**
> Which application is prefered for downloading videos from You Tube? Are community maintained software's available?

Install Download Helper in Firefox.  It's not FOSS.

---

### Post by scouser73 on 2009-09-04
> **Vinu Raj V said:**
> Which application is prefered for downloading videos from You Tube? Are community maintained software's available?

When you view videos or basically any content, you can find it in **/tmp** but the content will only be there while the browser is open.

So, once you have viewed a video you can then move it to a different folder.

---

