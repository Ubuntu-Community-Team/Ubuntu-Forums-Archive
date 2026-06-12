---
title: "Ubuntu acting like windows! Help!"
date: 2010-09-26
forum: General Help
---

### Post by dh04000 on 2010-09-26
Over the last week my ubuntu 10.04 install has been acting really weird. Its been slow to start and has been having random application crashes. Now, when I boot into ubuntu, at the log-in screen it gives me a pop-up window with the message "power-manager is not responding" and freezes. One in three times I log-in, it will freeze entirely and I have to reboot. Even when it lets me log-in, Ubuntu acts weirdly and the window manager will not show the minimize or maximize buttons.

I used synaptic to reinstall the gnome-power-manager, but it didn't help.

Is there a way to fix this, or reinstall gnome without losing all of my non-standard gnome applications?

---

### Post by sikander3786 on 2010-09-26
Are you sure you are not running out of space on your HDD?

---

### Post by dh04000 on 2010-09-26
Got 23+GB left.

---

### Post by sikander3786 on 2010-09-26
Try

```

sudo dpkg --configure gnome-power-manager

```


[COLOR="Red"]**EDIT:**[/COLOR] Also see this bug page. It might also be related to some usb device attached.

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862)

---

### Post by dh04000 on 2010-09-26
It turns out that it was the I-pod that was causing the problem. Its a first generation I-pod video. Why is it 6 months after 10.04 this simple bug is not fixed? How many people leave their I-pod left plugged in when they boot? Tons. I was charging my old dead one when I "discovered" this. This simple bug is inexcusable. Come on gnome/ubuntu devs!

---

### Post by harrismh777 on 2010-09-26
> **dh04000 said:**
> How many people leave their I-pod left plugged in when they boot? Tons. I was charging my old dead one when I "discovered" this. This simple bug is inexcusable. Come on gnome/ubuntu devs!

I generally do not have *any* usb memory modules plugged in when I boot... not even my digital camera. 

The first generation iPods were a fit... and they are a fit with linux. Don't leave them plugged in, and don't boot your system with them plugged in. Words to the wise.

Keep in mind that USB is "evolving". The first usb devices were trying to be compliant in keeping up with the evolving standard. Some of them succeeded better than others. 

Lastly, its not a simple bug. Could be a kernel thing, might be a driver thing, might be the usb hardware in your computer, might be the first gen iPod hardware or OS, and it might be you.   So... give the gnome ubuntu devs a break. How might you help them with the diagnosis?  Have you filed a bug report?


:)

---

### Post by maghoxfr on 2010-09-26
What a great title for the thread! IT's great because everybody relates unstability and slow performance with windows and it implies that ubuntu works better. Genius title.

---

### Post by dh04000 on 2010-09-27
> **harrismh777 said:**
> I generally do not have *any* usb memory modules plugged in when I boot... not even my digital camera. 

The first generation iPods were a fit... and they are a fit with linux. Don't leave them plugged in, and don't boot your system with them plugged in. Words to the wise.

Keep in mind that USB is "evolving". The first usb devices were trying to be compliant in keeping up with the evolving standard. Some of them succeeded better than others. 

Lastly, its not a simple bug. Could be a kernel thing, might be a driver thing, might be the usb hardware in your computer, might be the first gen iPod hardware or OS, and it might be you.   So... give the gnome ubuntu devs a break. How might you help them with the diagnosis?  Have you filed a bug report?


:)


Ok... it might now be a simple bug, but it saddens me that a long-term support, flag ship enterprise, ubuntu release still has this bug after its been reported close to six months. Tons of people do leave usb cameras, mice, i-pods, storage sticks plugged in at boot. A trip to any college dorms can confirm that, lol.

Ummmmm.... I have no idea how to fill a bug report. I saw that you posted a link to a bug report. Got no idea how to add myself. Its a confirmed bug, so adding myself won't help I'm sure.

Any idea if the dev. branch of gnome-power-manager has the fix? Can it be backported by ubuntu dev's?

I just want ubuntu to succeed. Bugs needs to be crushed! :p



> **maghoxfr said:**
> What a great title for the thread! IT's great because everybody relates unstability and slow performance with windows and it implies that ubuntu works better. Genius title.



I make my titles to grab attention. One time I had a problem with pidgin, and after posting it twice, no one helped me on this board. So, I reposted with the title "Help! My pidgin has bird flu", and got help in minutes. Making catchy or attention grabbing titles can help you get help. Also, it is irronic cuz I had just finsihed fixing an instability problem on windows the week before, that related to boot, so the title fitted, lol.

---

### Post by Banned. on 2010-09-27
> **maghoxfr said:**
> What a great title for the thread! IT's great because everybody relates unstability and slow performance with windows and it implies that ubuntu works better. Genius title.

True!

Also, when I used to use Windows, it would give me BSOD sometimes if I had USB plugged in while starting. I think Ubuntu is better at it because it even starts the computer.

I have windows 7. People say it is very good. I liked it first day but I forgot that any version of trash is still trash. It is certainly better than Vista but not significantly better.

@OP, I'm sorry to hear that but I also want something from gnome. I want GDM that can be themed, like some versions before. But now I let it go because everything else is beyond awesome!

---

### Post by Quackers on 2010-09-27
As I have found previously, it's not the best idea to have usb devices plugged in at boot. They can cause many problems including various forms of crashes. At the very least they can cause an increase in boot time.

---

### Post by dh04000 on 2010-09-27
> **Banned. said:**
> 
@OP, I'm sorry to hear that but I also want something from gnome. I want GDM that can be themed, like some versions before. But now I let it go because everything else is beyond awesome!

I already complained about not being able to theme Plymouth and the new gdm. I told the 100 paper cuts crew that I found that plymouth and gdm not being themable(without some nasty cli hacks) was annoying and I wished for a gui. The next respond on the paper cut board was "users" were the biggest papercut(referring to me). So there is no hope in that department. Noone cares.

---

### Post by Banned. on 2010-09-27
> **dh04000 said:**
> I already complained about not being able to theme Plymouth and the new gdm. I told the 100 paper cuts crew that I found that plymouth and gdm not being themable(without some nasty cli hacks) was annoying and I wished for a gui. The next respond on the paper cut board was "users" were the biggest papercut(referring to me). So there is no hope in that department. Noone cares.

That's very disappointing!

However, I have changed my plymouth theme. Look here.
[http://answers.yahoo.com/question/index?qid=20100415083349AAiNjRf](http://answers.yahoo.com/question/index?qid=20100415083349AAiNjRf)

I didn't ask that question, however. I just googled it :)

I am using this theme:
[http://gnome-look.org/content/show.php/Space-Sunrise+Plymouth+Splash?content=129678](http://gnome-look.org/content/show.php/Space-Sunrise+Plymouth+Splash?content=129678)

EDIT: There is a .deb file in the link I posted. It will install the theme and you won't need to do tweaking! It will not show as installed though.

---

### Post by maghoxfr on 2010-09-27
> **Quackers said:**
> As I have found previously, it's not the best idea to have usb devices plugged in at boot. They can cause many problems including various forms of crashes. At the very least they can cause an increase in boot time.

I didn't know that but it explains why it's taking so long for my machine to boot, I have 4 USB devices hooked to it permanently. It's very annoying to plug/unplug them everytime I restart it. But good to know.

---

