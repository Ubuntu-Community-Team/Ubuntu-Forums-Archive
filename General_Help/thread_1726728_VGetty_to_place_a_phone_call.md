---
title: "VGetty to place a phone call"
date: 2011-04-11
forum: General Help
---

### Post by Dudeman02379 on 2011-04-11
I am trying to setup vgetty to be able to place a phone call and play a pre-recorded message on ubuntu server 10.04.  Once I have this working I am going to use it as part of a network monitoring system.

I found two articles that I tried following but I am running into problems. Here are the two articles
[http://www.webreference.com/perl/tutorial/14/2.html]("http://www.webreference.com/perl/tutorial/14/2.html")
[http://www.lckdanny.com/wordpress/?p=80]("http://www.lckdanny.com/wordpress/?p=80")

I was able to install mgetty, mgetty-voice, and mgetty-docs

I was also able to use vm record to record a message file and vm play will play it back.

I can use vm -dial {phone number} and the modem will call the number.

However when I create the perl script that is described in the above links and try to run ```
vm shell -l ttyS0 -S simple_alert.pl
``` it does not work.

Do I need to install Perl or another mgetty piece?  Or am I possibly missing some configuration steps?  Any help would be appreciated.

Thanks!

---

### Post by Dudeman02379 on 2011-04-12
no one?  I feel like it is very close to working because I can record a message or make the modem dial.  I just need some help getting the scripting feature to work. There really aren't any good online resources to help me figure this one out.

---

### Post by rylangrant on 2011-04-13
I followed this: [http://shrewdraven.org/content/setting-mgetty-dialout-and-send-audio-message-under-linux](http://shrewdraven.org/content/setting-mgetty-dialout-and-send-audio-message-under-linux)

Before doing this, I couldn't even get mine to dial. Now it dials the number fine but won't play the audio file. I have a "Modem returned ERROR" in my /var/log/vm.log file so I have a feeling its tied to that. I'll post back once I know more.

---

### Post by Dudeman02379 on 2011-04-25
Has anyone had any experience with getting ubuntu to dial a phone number and play a pre-recorded message?  I'm open to any recommendations.

---

### Post by Dudeman02379 on 2011-04-27
Figured it out.  Thanks for all the help.....

---

