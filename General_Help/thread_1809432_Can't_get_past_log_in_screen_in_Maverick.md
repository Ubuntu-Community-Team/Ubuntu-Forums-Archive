---
title: "Can't get past log in screen in Maverick"
date: 2011-07-21
forum: General Help
---

### Post by medusa569 on 2011-07-21
One day I started my computer and it successfully goes into the GUI login screen and starts to load the generic display preferences ( as I can see by the lower task bar ) but then it will quickly flicker and then kick back to the GUI login screen.  I can log in to the terminal screen (ctr +alt+f1) but I don't know what I can do from there. 
Help please.......




medusa

---

### Post by galvatron408 on 2011-07-22
well, if you can get on to the command line, take a look at the log to see what it's complaining about.

just do....

"sudo tail -100 /var/log/messages"

alternatively, just type "dmesg"

if you need help, post it back here and i'll try to help you.

---

### Post by 2F4U on 2011-07-22
The file .xsession-errors in your home directory may also contain important information.

---

### Post by medusa569 on 2011-07-22
> **galvatron408 said:**
> well, if you can get on to the command line, take a look at the log to see what it's complaining about.

just do....

"sudo tail -100 /var/log/messages"

alternatively, just type "dmesg"

if you need help, post it back here and i'll try to help you.



I get a whole bunch of info that rapidly scrolls past...how can I do a screen by screen feed of the dmesg command?
ON the meanwhile when i did that the last line showed from apparmore Denied operation  profile/usr/share/gdm/guest-session/xsession     name=home/medusa569/.profile   denied mask.....

---

### Post by galvatron408 on 2011-07-22
You can redirect the output to a file and then use vi to look at it

for example:
dmesg >> /tmp/myoutput.out

or.... to do a screen by screen, 

dmesg | less

(use Ctrl+f and Ctrl+b for page up and page down, to exit, press esc and then press q)

---

### Post by medusa569 on 2011-07-22
> **galvatron408 said:**
> You can redirect the output to a file and then use vi to look at it

for example:
dmesg >> /tmp/myoutput.out

or.... to do a screen by screen, 

dmesg | less

(use Ctrl+f and Ctrl+b for page up and page down, to exit, press esc and then press q)



I did the more dmseg command and was able to control it.....again to my knowledge not knowing how well to spot problems in this file I only see the Xserver message that seems it would control that login for my personal desktop.

---

