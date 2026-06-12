---
title: "Novaterm Failed To Connect (Palm Pre Related)"
date: 2009-11-02
forum: General Help
---

### Post by crazy_lazy_bear on 2009-11-02
Hello All,

     I am trying to access root of my Palm Pre.  I have installed palm-sdk, virtualbox, and novacomd.  I am following the instructions on this web page: [http://www.webos-internals.org/wiki/Accessing_Linux_Using_Novaterm](http://www.webos-internals.org/wiki/Accessing_Linux_Using_Novaterm)

     I located novaterm in /usr/local/bin.  When I run "novaterm", "./novaterm", or "novacom $* -t open tty://0" in terminal, I receive a "failed to connect to server" message.  The instructions in the website above say, for a Mac, to run:

sudo chmod 644 /Library/LaunchDaemons/com.palm.novacomd 
sudo launchctl load -w /Library/LaunchDaemons/com.palm.novacomd 
./novaterm

     I do not know enough about the "chmod" command nor Macs to understand what I should do in Ubuntu.  Any suggestion are greatly appreciated.  Thanks.

---

### Post by crazy_lazy_bear on 2009-11-02
bump

---

### Post by spillin_dylan on 2009-11-02
Well the Mac instructions sure won't help you in Ubuntu, as there is an almost near guarantee there is no "/Library/LaunchDaemons/com.palm.novacomd" anywhere in your filesystem.  

I'm not sure why your Pre is giving you a failed to connect message, are you sure you followed the how-to?  I definitely was able to gain root on mine using the steps outlined on that page.  Make sure you keep going on to Page 2, where you set up a user for yourself and an ssh server so you don't have to "break in" as root every time!

The "chmod 644" part of the syntax is going to make that file read-only to everyone except the owner, who can also write to it, but I don't think that's necessary in Ubuntu.

---

### Post by crazy_lazy_bear on 2009-11-03
Hello All,

     I also posted this question in precentral.net.  A member posted this link: [https://developer.palm.com/distribut...hp?f=31&t=1391](https://developer.palm.com/distribut...hp?f=31&t=1391)

     I looked at the explanation of the work-around. I just need a little more help: The explanation states:

then "sudo palm-novacom/opt/Palm/novacom/novacomd &" to start the novacom daemon, and put novacom and novaterm somewhere in your path (but NOT in /usr/local/bin else it will cause problems when you try to install the next update).

When I run "sudo palm-novacom/opt/Palm/novacom/novacomd &", I get "[1] 4840". When I run "novaterm", I get "[1]+ Stopped sudo palm-novacom/opt/Palm/novacom/novacomd."

I don't understand the instructions to "put novacom and novaterm somewhere in your path (but NOT in /usr/local/bin else it will cause problems when you try to install the next update)".

If someone could provide some more granular instructions, it would be greatly appreciated. Thanks.

---

### Post by crazy_lazy_bear on 2009-11-03
Hello All,

     I got it working.  I had to reset my Pre.  It wouldn't even update Pandora.  Thank you for your help.

---

