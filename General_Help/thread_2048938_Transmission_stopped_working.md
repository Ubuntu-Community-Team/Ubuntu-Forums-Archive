---
title: "Transmission stopped working"
date: 2012-08-27
forum: General Help
---

### Post by uzumakifahim on 2012-08-27
Hi everybody,
suddenly my Transmission stopped working. It's not making any connection with any peers. Two of my downloads which are 25% and 48% suddenly stopped, though the health of good enough (more than 150 seeds and peers). Not only that new torrent files are also unable to connecting with other peers. My INTERNET connection is perfectly OK. No problem with any other type downloading and browsing. 

I am using Ubuntu 12.04 and Transmission 2.51. Please anyone help me in this regard.

Thanks in advance.

---

### Post by Cheesemill on 2012-08-27
Perhaps your ISP is blocking / traffic shaping bittorrent traffic, I've seen that happen several times before.

Check with your ISP and see what they have to say.

---

### Post by uzumakifahim on 2012-08-28
Thanks for your reply. I thought it's issue regarding ISP. That's why I've observed the issue in several ways.

1. My PC is dual booted with windows 7. When Transmission stopped working then I went to Windows 7 and run qbittorrent and it was perfectly OK. It was downloading with full speed. 
2. Then I came to Ubuntu and install qbittorrent here and open the same torrent file which is completely inactive in Tranmission and the result is qbittorrent works perfectly good here as well.

Now I don't understand what is the problem with Transmission. I need to solve this problem. Please anyone help.

---

### Post by alan21276 on 2012-08-28
Have you tried using a different port in the settings?

Also try purging transmission and re-installing.

---

### Post by coldcritter64 on 2012-08-28
OP, before doing anything like reinstalling, try running transmission from the terminal, and copy/paste and post any errors back here, there will likely be some by the sound of this question.

Open a terminal and use,
```
transmission-gtk
```It is possible you may have something like an stale lock file for transmission not removed. Simply deleting a stale lock file has helped me in the past to get it going again. Getting some error information and posting it here will likely help you.

Edit: I may have misread your original post OP, will the program itself start? If so, ignore this post. Sorry. I read that as the program failing, now see it may mean just the torrents.

---

### Post by uzumakifahim on 2012-08-29
@ [alan21276]("http://ubuntuforums.org/member.php?u=1323420") 

No. I haven't tried with any other port. Which port is that and how can I do that? Please tell me.

---

### Post by alan21276 on 2012-09-05
The port settings are under Transmission preferences-Network

try the test port button to see if your current port is open, if not then try different port's. A quick search on Google can offer some suggested port's (dependant on local or router firewall settings)

I remember having trouble with transmission last year and my usual fix of changing the port made no difference even if detected as open, a purge and re-install was the quickest and easiest way to fix it.

Sorry for taking so long to get back to you.......my house got flooded last week.

---

