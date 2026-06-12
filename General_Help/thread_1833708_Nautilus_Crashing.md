---
title: "Nautilus Crashing"
date: 2011-08-26
forum: General Help
---

### Post by Dasien on 2011-08-26
Hello,
I am not sure what I have done but recently Nautilus seems to be crashing it has to be forced to quit every time I shut down and I can not open it in gui. When I run it from terminal I get this message.

"(nautilus:7942): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I have read the posts about opening a image in inkscape and saving it as a .jpeg instead of a .svg but I don't think this is my problem because I have deleted all of my photos and I don't think there is any conflict. I did have some luck when I deleted one image I was using as My background and it seemed to fix the problem until I restarted the computer. 

I am running Naughty on my eepc 1000ha

Thanks
Nick

---

### Post by Dasien on 2011-08-26
I have also noticed how I can save things to the desktop but nothing seems to appear on the desktop, but it does exist within the folder?
Nick

---

### Post by drpjkurian on 2011-08-26
Hi 
open the desktop folder and select the option view hidden files

---

### Post by drpjkurian on 2011-08-26
Hi
You can try```
sudo nautilus
```
Are you using still using Hardy

---

### Post by Actonix on 2011-08-26
Have you checked your boot messages to se if that indicates any possible problems ?

```

sudo dmesg -n 1

```

---

