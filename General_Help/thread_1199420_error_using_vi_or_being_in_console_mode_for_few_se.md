---
title: "error using vi or being in console mode for few seconds"
date: 2009-06-28
forum: General Help
---

### Post by gabak on 2009-06-28
[79254.685540] b43-phy0 ERROR: PHY transmission error.
when i m trying to edit or create a text that message appear from nowhere and i dont know what to do , what does it mean?
it is very annoying cuz it appear on the text i m creating
and make do weird thing on vi

---

### Post by akakingess on 2009-06-28
So just to clarify, you are simply typing a text document and this error message comes up? What are you using to create the text file? Also, have you googled that exact error message, you would be surprised cuz the answer may be in that message. Let me know what you find out.
 
akakingess

---

### Post by gabak on 2009-06-28
yes i did
i googled and i could nt find the same error
i was trying to make a little script with vi or vim
and that error shows up after 20 seconds aprox. of being typing
even if i dont type anything it will show up suddenly
i saw other ppl on google they have that problem with the wifi card
but in this dell laptop d610 i disconected the wifi card to work off line
and it still happen

---

### Post by linuxmagick on 2009-06-28
Just for the heck of it, have you tried disabling IPv6 like one of the people mentions in this thread:  [http://ubuntuforums.org/showthread.php?t=935253]("http://ubuntuforums.org/showthread.php?t=935253")?  

The b43 part of the error seems to signify a Broadcom driver, so it may still be related in some way to your wireless card.  I would try disabling IPv6 and see if it helps at all.

Actually, the method for disabling IPv6 in the above link won't work for Jaunty.  So instead you may be interested in this:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263106]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263106")

---

### Post by gabak on 2009-06-28
i did that but i dont see aliases file to modify. (i m using ubuntu 9)

1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
4. Reboot Ubuntu.

---

### Post by linuxmagick on 2009-06-28
Yeah, sorry.  I had just updated my last post because I realized that won't work for Jaunty.  

It just occurred to me to try the simple approach.  Try adding ```
blacklist b43
``` to /etc/modprobe.d/blacklist.conf.  This should blacklist the b43 module and keep it from loading.  I guess I should ask if you ever do use the wireless connection?

---

### Post by gabak on 2009-06-29
it is done
do i have to restart ubuntu? now
about ur question yes i do use wireless connection all the time
24/4
why?

---

### Post by linuxmagick on 2009-06-29
Yes, you'll need to reboot.  

I was asking whether or not you used the wireless because blacklisting that module should cause the wireless not to work.  

If this fixes your original error, you will want to look at the bug report link that I added to my earlier post.  It may help.  You will need to remove the blacklist line that you just added and reboot again to get the wireless functionality back.

---

### Post by gabak on 2009-06-29
hi
yes this worked but i had no wifi jeje
muerto el perro muerto la rabia !
well i think there is a way to send all the errors to dev/null or something like that.
thank you for your help , but i think have to be other way to fix that.

---

### Post by bab1 on 2009-06-29
> **gabak said:**
> [79254.685540] b43-phy0 ERROR: PHY transmission error.
when i m trying to edit or create a text that message appear from nowhere and i dont know what to do , what does it mean?
it is very annoying cuz it appear on the text i m creating
and make do weird thing on vi

This appears to be a problem with the wireless card.  ```
b43-phy0
```
This can be a kernel problem or a Network Manager problem. 

See here: [**_https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199191_**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/199191")

here is my Google search on the subject: [**_http://www.google.com/search?hl=en&q=vim+%2B%22+PHY+transmission+error%22&aq=f&oq=&aqi=_**]("http://www.google.com/search?hl=en&q=vim+%2B%22+PHY+transmission+error%22&aq=f&oq=&aqi=")

---

### Post by linuxmagick on 2009-06-29
Not sure if you looked at [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/263106]("https://bugs.launchpad.net/ubuntu/+s...ux/+bug/263106").  
Read the last post there.

There are a couple of directories you can try to download and replace on your system.  This seems to have fixed the b43-phy problem for several users.

---

