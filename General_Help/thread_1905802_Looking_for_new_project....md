---
title: "Looking for new project..."
date: 2012-01-07
forum: General Help
---

### Post by Dragonpoet on 2012-01-07
Hello all! I am here looking for advice on what to do next. I am fairly new to Ubuntu. I want to be able to understand stuff.

A little about me: I am coming from Windows. It's the only operating system I've really ever know well. But as I want to make a career change into the IT field, I figure I'd better go ahead and venture out on my own and see what I can learn. I am currently dual booting with Windows 7 on a Dell Inspiration 1764 laptop.

What I know: I've managed to:
- Change grub2 so that Windows 7 is the default OS
- Change grub2 time out to 3 seconds
- Automount a shared partition called "Storage"
- Moved Documents, Pictures, Videos, Downloads, and Music folder locations to "Storage"
- Run apt-get update

So let me ask some questions to hopefully help you help me. :p
- Is there any maintenance that I have to do such as "defrag" or "disk cleanup"?
- Do you have any ideas on how I can customize my system.a
- How have you customized your system?

I know I am being very veg, but that's because I want to learn, although I don't know what TO learn if that makes any sense. I like to do more of a hands-on approach to this because when I read something, I generally have to read it about 3 or 4 times. Thank you for reading this and thank you for the help in advance.

---

### Post by Basher101 on 2012-01-07
answer to question one: none. The ext4 filesystem Ubuntu uses must not EVER be defraged. EVER. The only thing you should do from time to time would be ```
sudo apt-get autoremove
``` to clean out installation left-behinds...

answer to question two: [http://news.softpedia.com/news/Ubuntu-11-10-Desktop-Customization-Guide-242549.shtml](http://news.softpedia.com/news/Ubuntu-11-10-Desktop-Customization-Guide-242549.shtml)

answer to question three: [http://ubuntuforums.org/showthread.php?t=1889046&highlight=december+screenshots&page=24](http://ubuntuforums.org/showthread.php?t=1889046&highlight=december+screenshots&page=24) post # 234


regards

---

### Post by d3v1150m471c on 2012-01-07
> answer to question one: none. The ext4 filesystem Ubuntu uses must not EVER be defraged. EVER. The only thing you should do from time to time would be 

right, fsck should do any necessary repairs every 20 boots.

---

### Post by pretty_whistle on 2012-01-07
sudo apt-get clean

That removes the aptitude cache in /var/cache/apt/archives.

---

