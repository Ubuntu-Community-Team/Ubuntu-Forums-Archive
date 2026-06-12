---
title: "Compiz crashed everything!"
date: 2006-06-19
forum: General Help
---

### Post by Crashmaxx on 2006-06-19
So I tried to install compiz again. This time with the automated script someone had here. It didn't have borders on the windows though. So I tried a few other things and now the gdm won't start. It just has a dotted tan screen with the cursor loading. I can still use recovery mode, but only the command prompt. I'm using a dapper live cd right now. I can't use windows xp either. When I boot it, it just locks up at the desktop and I can't open anything.

So any ideas how to remove compiz or what I need to do to get ubuntu to work again?

Thanks, and a few details you might want. Its a dell 600m and I'm running Ubuntu 6.06 with a dual boot of Windows XP. It has a Pentium M 1.6 GHz processor with a 64mb ATi 9600 graphics card and 512mb of ram, and a 60 GB hard drive.

---

### Post by woedend on 2006-06-19
i would start by disabling xgl and making compiz unexecutable.  
in command line, do
sudo vi /etc/gdm/gdm.conf-custom

delete everything under and below the line [servers]
then save

if you've never used vi before, you must push the insert key to begin typing/removing/changing things...use the arrows to scroll around.  when you are done, push escape, then push colon ( : ), then type wq and push enter.  so, you would arrow down to the bottom/end of the file, push insert, hold down backspace until the last thing left is [servers], push escape, then type     : w q    and push enter

 This will keep xgl from loading. 

 As for compiz, make in inexecutable by using chmod.   if you used "thefuture" script, do
sudo chmod -x /usr/bin/thefuture

assuming thats where you made the file.

then reboot.
good luck

---

### Post by Crashmaxx on 2006-06-19
Thanks so much man. I couldn't remember what was still running to mess it up. What do I need to do to get rid of the XGL session I made and anything else I need to do to remove the rest of compiz?

---

### Post by iluva on 2006-06-19
if you aren't @ home in the console and vi(m) etc. there is an easier way to get rid of compiz and XGL.
start live cd, -> console
> sudo aptitude remove xserver-xgl compiz
 or use synaptics if this works

---

### Post by woedend on 2006-06-19
the xgl session is loaded through the GDM(where you login, type in your name/password/etc.  The first step in my post returns this to default(no xgl).
The second step keeps compiz from running.
That will leave you with nothing xgl related running, although it is on your system dormant(causing no harm).  If you want to remove it completely to feel better, follow what iluva has outlined

---

