---
title: "VirtualBox"
date: 2012-02-19
forum: General Help
---

### Post by qwertyjjj on 2012-02-19
I have VB installe don 11.10 and just added the guest additions.
I can't seem to see the Machine, and other menu items at the top to change the scale and the scale is a little off normal resolution.
How can I get full screen in VB or how can I see these menu options?

---

### Post by Ms. Daisy on 2012-02-19
You have to hover your mouse over the toolbar for the menu to show up. Does that work?

I resize my VMs by clicking on the maximize button or expanding it manually by clicking & dragging on the bottom corner. Does that work?

---

### Post by qwertyjjj on 2012-02-19
> **Ms. Daisy said:**
> You have to hover your mouse over the toolbar for the menu to show up. Does that work?

I resize my VMs by clicking on the maximize button or expanding it manually by clicking & dragging on the bottom corner. Does that work?

No menu appears.
I can resize it but something is wrong with the resolution when I do that - it just looks slightly wrong like the text is stretched somehow or the res is wrong. In Meerkat it worked fine but I can't seem to get the optionn for scale in 11.10

---

### Post by wildmanne39 on 2012-02-19
Hi, she meant the top panel in ubuntu, when you hover your mouse which ever window that is opened should show up.

I have a lot of trouble with scale mode in 11.10.
Thanks

---

### Post by qwertyjjj on 2012-02-19
> **wildmanne39 said:**
> Hi, she meant the top panel in ubuntu, when you hover your mouse which ever window that is opened should show up.

I have a lot of trouble with scale mode in 11.10.
Thanks

just a blank panel with the minimise, maximise, close buttons shows

---

### Post by Ms. Daisy on 2012-02-19
Thanks Wildmanne- that's what I meant. I'll post a screenshot in a minute.

Hmm... I don't have any trouble scaling my virtualbox VMs on an 11.10 host.  I can make them long & skinny or whole screen with no problems.  Which version are you running? I'm running VB from the oracle website 4.1.8, not the one in the ubuntu software center. I wonder if that makes a difference.

---

### Post by qwertyjjj on 2012-02-19
> **Ms. Daisy said:**
> Thanks Wildmanne- that's what I meant. I'll post a screenshot in a minute.

Hmm... I don't have any trouble scaling my virtualbox VMs on an 11.10 host.  I can make them long & skinny or whole screen with no problems.  Which version are you running? I'm running VB from the oracle website 4.1.8, not the one in the ubuntu software center. I wonder if that makes a difference.

but i can't even list the options to scale or full screen or anything else?

---

### Post by wildmanne39 on 2012-02-19
Hi, you may need to reinstall guest additions if you can not go full screen.

What version of virtualbox are you using?

I can not get on my desktop with unity and virtualbox to check it and post screenshots at this time because I cracked my knee cap a few days ago and I have to stay in bed so I am working from memory only.
Thanks

---

### Post by Ms. Daisy on 2012-02-19
> **qwertyjjj said:**
> but i can't even list the options to scale or full screen or anything else?
I can't answer that question until I know the answer to this: How did you install virtualbox?

As far as the menu goes, this first screenshot shows the top bar as it appears when you've got a VM running. The virtualbox window has the mouse focus. You can't see my pointer but it was hovering over the vm. Note the area that the red arrow is pointing to.
 [IMG]http://3.bp.blogspot.com/-3HBr-lBQwmA/T0FcktB-RKI/AAAAAAAAACY/JJItmRrUEGk/s320/Workspace+1_001.png[/IMG]

This next screenshot shows the top bar when you hover your mouse over the top bar while the vm is running. Again you can't see my pointer but it was hovering over the very top black/gray bar. Note the area where the white arrow is pointing.
[IMG]http://2.bp.blogspot.com/-WtHWLExdHTg/T0FclxBW9uI/AAAAAAAAACg/OVOmmFxbxZc/s320/Workspace+1_002.png[/IMG]

So if you can't see those then you may have mouse capture issues.  When you click on the VM, what happens? Is your mouse captured and you can no longer click on the host desktop until you push right ctrl?

---

### Post by Ms. Daisy on 2012-02-19
@ wildmanne- yikes! I'll do the screenshots for you! Just name it.

---

### Post by wildmanne39 on 2012-02-19
Hi Ms. Daisy, I appreciate the offer.
Thanks

---

### Post by qwertyjjj on 2012-02-19
v4.1.2

[IMG]http://img69.imageshack.us/img69/7166/header1yf.png[/IMG]

---

### Post by wildmanne39 on 2012-02-19
Hi, I think the problem is that you are using an old version of virtualbox not updated for 11.10 if you upgrade vb to the lateest version I think it will fix your problem.

Did you get rid of the global menu in 11.10?

Also in the newer virtualox it puts a menu at the bottom of the screen also that you can be used to change to scale mode and much more.
Thanks

---

### Post by qwertyjjj on 2012-02-19
Just installed 4.1.8, same problem though.
When the main VB window is selected and I hover on the top bar there is no menu to do with anything inside VB. I used to have something where I could even select the USB peripherals but not anymore.

---

### Post by wildmanne39 on 2012-02-19
Hi, > Did you get rid of the global menu in 11.10?

Are you logged into unity? or fallback mode or gnome shell?
Thanks

---

### Post by Ms. Daisy on 2012-02-19
I don't have the slightest idea why you wouldn't have the toolbar.  In my expert opinion (ha ha), it's broken.

I battled with virtualbox for about a month before I decided to install the one from the oracle website instead of the one in the software center. Life has been much much easier since I switched.  If you're interested in going that route I created a small [checklist ]("http://ubuntuforums.org/showthread.php?t=1916076")that may help.

edit: answer Wildmanne's question first though.

---

### Post by guestolo on 2012-02-19
It's possible that you are in Scale mode

Try pressing your Host + C keys, typically Right Ctrl + C key

This is the typical warning you get when switching to Scale mode

=================================================
    The virtual machine window will be now switched to Scale mode. You can go back to windowed mode at any time by pressing **Host+C**.
 Note that the *Host* key is currently defined as **Right Ctrl.**
 Note that the main menu bar is hidden in scale mode. You can access it by pressing **Host+Home.**

---

### Post by qwertyjjj on 2012-02-20
> **guestolo said:**
> It's possible that you are in Scale mode

Try pressing your Host + C keys, typically Right Ctrl + C key

This is the typical warning you get when switching to Scale mode

=================================================
    The virtual machine window will be now switched to Scale mode. You can go back to windowed mode at any time by pressing **Host+C**.
 Note that the *Host* key is currently defined as **Right Ctrl.**
 Note that the main menu bar is hidden in scale mode. You can access it by pressing **Host+Home.**

Can;t get out of scale mode then.
Nothing happens when pressing right ctrl c
It's the latest VB from the oracle site and repos.

---

### Post by mastablasta on 2012-02-20
*right crtl+f* should switch it to full screen. 
 
it will thrown the menu on the bottom.

---

### Post by qwertyjjj on 2012-02-20
> **mastablasta said:**
> *right crtl+f* should switch it to full screen. 
 
it will thrown the menu on the bottom.

That did the trick.
Thanks

---

