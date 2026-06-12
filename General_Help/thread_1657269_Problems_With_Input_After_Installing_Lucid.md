---
title: "Problems With Input After Installing Lucid"
date: 2011-01-01
forum: General Help
---

### Post by Víkþórr Veggiss Berurjóðr on 2011-01-01
I installed Lucid today, having used my favourite (but, sadly, long discontinued) distro, Intrepid, until now. I had this problem when I tried upgrading to Jaunty as well, which was one of the reasons I just stuck with Intrepid back then. So, my setup in Intrepid was pretty straightforward; I used xmodmap to change several functions on my keyboard, most notably removing caps lock and adding several dead keys. I also set up SCIM for inputting IPA and Asian languages, and it worked without any problems whatsoever.

However, when I tried the same setup in Lucid, I first encountered a problem with xmodmap. At first, I thought it simply didn't load at boot, even though I had set it to do so, but then I realized that it did load, but caps lock wasn't gone (I don't know why – it goes away when I run "xmodmap .Xmodmap" manually, but it's back when I reboot), and the dead keys didn't work after I installed SCIM (which was also less straightforward than in Intrepid, but I got it to work).

I tried a number of different things, but whenever I got the dead keys to work, SCIM stopped working, and whenever I got SCIM to work, the dead keys stopped working! I came across [this thread]("http://ubuntuforums.org/showthread.php?t=798426"), and I deleted my ~/xinput.d, but I guess that wasn't very smart. How can I remove a symlink, or even check to see if it's there at all? Should I make a new ~/xinput.d? If it proves impossible to fix, I *can* write most of the diacritics using SCIM and the IPA input, but that's very inconvenient.

So, in summary, my problems are:
1. Getting dead keys and SCIM to work alongside each other.
2. Getting caps lock to NOT reappear every time I boot up the computer.

Thanks in advance! :)

---

### Post by manat2 on 2011-01-01
Hi, I am Moris here, I am facing the problem in Input .I installed Lucid today, having used my favourite. I had this problem when I tried upgrading to Jaunty as well, which was one of the reasons I just stuck with Intrepid back then. So, my setup in Intrepid was pretty straightforward; I used xmodmap to change several functions on my keyboard..........Please provide  some information regading same........Thanking you.

---

### Post by Víkþórr Veggiss Berurjóðr on 2011-01-02
I fixed problem number one, which was the most pressing one. :)

All I had to do was to go to System > Administration > Language Support, select Input Method > scim-bridge, and reboot. :D

Now I only need to find a way to make caps lock stay dead when I reboot.

---

