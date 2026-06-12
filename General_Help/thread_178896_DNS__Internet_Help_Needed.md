---
title: "DNS / Internet Help Needed"
date: 2006-05-18
forum: General Help
---

### Post by StubornAH on 2006-05-18
Hello,

I don't know much about Linux, so I am asking for some help.  I took a class on computer networks and know how they work in theorey, but theory and practice are different.  So, feel free to use whatever terms you like, just don't go too fast.

Now, the problem is with my desktop.  I can ping google.com but I can't get there with Firefox.  I can ping any site I can think of.  The only page I have successfully loaded in Firefox is the Ubuntu site.  I can explore that site as much as I like, but when I try to go to a different site it no longer works.  By "not working" I mean that at the bottom of the Firefox window it says Connecting to [www.google.com](www.google.com)...  for about 5 minutes and then it gives me an error saying it failed to connect.

How can I further troubleshoot this problem?  Or if someone knows the solution, that is good too.

Thanks


PS  it sounds like there is a new version of Ubuntu, if it helps I am using Badger that I installed about 6 months ago.  I just haven't taken the time to fix my problem.

---

### Post by Slim Odds on 2006-05-18
Have you tried any other browsers?

Try epiphany or anything else.

It sounds like you might be having the classic "Firefox and IPV6" problem. Do a search for that.

Does the update manager work?

---

### Post by StubornAH on 2006-05-18
I get the symbol saying there are available updates but I didn't wait long enough to see if it would actually work.  I was reading a similar thread and tried ifconfig, it listed both an IPv4 and an IPv6 address, so I think I will look that up.

Thanks

---

### Post by dg_w on 2006-05-18
ok first update

logout of gnome ... then press CTRL+ALT+F3
login and do
sudo apt-get update
sudo apt-get dist-upgrade
after done reboot 

ok once rebooted, try again :)
make sure your /etc/resov.conf is correct

ie 

nameserver "your router ip address"
nameserver 158.152.1.43

---

### Post by StubornAH on 2006-05-18
I disabled IPv6 in Firefox and it works fine now.

Here is the page I found about IPv6 and Firefox:
[http://techpatterns.com/forums/about373.html](http://techpatterns.com/forums/about373.html)

Thanks again for the help, I even contacted a Unix admin friend of a friend and he had no idea...

---

