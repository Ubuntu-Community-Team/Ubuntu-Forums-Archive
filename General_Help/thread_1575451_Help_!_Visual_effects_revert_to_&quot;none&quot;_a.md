---
title: "Help ! Visual effects revert to &quot;none&quot; all the time"
date: 2010-09-15
forum: General Help
---

### Post by sl789 on 2010-09-15
I have dell XPS studio desktop with GeForce 7900 GS. Driver version is 173.14.22.
My version of ubuntu is 10.04 fresh install

Recently "Appearance"->"Visual Effects" settings reverts ALL THE TIME to "none".
Sometimes it happens each minute, sometimes it's OK for few hours. 
I need to rest it back ( It takes 20-30 sec when a window appears "looking for drivers"
then " would you like to keep current setting".

It comes to the point when ubuntu becomes unusable. I didn't have this problem with 9.10
I tried to upgrade to a current version of Nvidia drivers but then Gnome fails.

I read a lot about similar problem ( reverts to "none" after each reboot ), but i my case it reverts ALL THE TIME - Suddenly windows borders disappear etc. In Wiki how there is a remark about bug in Nvidia drivers. 

Any advices/helps ?

I found on the web that sometimes such aproblem might be caused if memory on Graphic Card gets corrupted. Anybody now about the tool I can install - Ubuntu or Windos (I have double boot) to test it ?

Thnaks in advance

---

### Post by ngrieb on 2010-09-16
You might have already tried this, but after resetting them to how you want next time try and save the currently running programs in your startup programs toolbox. If that doesn't do the trick let me know.

---

### Post by sl789 on 2010-09-16
Ngrieb, thanks for advice

I'll definitely try it today when I back home.

What's really frustrating that this a well-known problem ( at least reverting to "none" after reboot) and it's known for a long time that there are bugs in latest version of Nvidia driver
(there is a warning on wiki page), but NOTHING is done. No new version of the driver ( for a long time), not a hack from Xorg nothing ! 
It's the first time in many years that I consider go back to Windows despite extreme desire not to do so.

---

### Post by sl789 on 2010-09-16
I found the following bug 

[https://bugs.launchpad.net/ubuntu/+bug/563023](https://bugs.launchpad.net/ubuntu/+bug/563023)

googling for  "visual extras reverts to none searching for available drivers"

and per recommendation of one of the participants 
I've reinstalled compiz and compiz-gnome

Didn't help. Extremely frustrating. There are hundreds of references to this problem going back many months ( I beleive more then a year or even two) and nobody knows the reason or the solution. Sometimes reinstallations of different packages helps, sometimes not

Is it any way to elevate this and bring to the attention of ubuntu developers ?

---

### Post by supershin on 2010-09-16
Nvidia graphic cards are not very well supported it seems. I have a different problem, couldn't get extra option using the latest nvidia driver, and found more problems about nvidia cards in lucid. 

A search of the forum/net will highlight these. They should know already since its in the list.

---

### Post by sl789 on 2010-09-17
Supershin , as to the 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

The latest Nvidia driver has a bug here is quotation

"Due to a bug see [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997) .The NVIDIA driver may not work . "

I've seen this warning many months and apparently NOTHING has been done. Neither fix by Nvidia, nor hack by Ubuntu. Well, the software is free so you got what you paid for.

I start questioning the whole concept of the "free software", since If I can't use and neet to waste huge amount of time  it's not "free" by definition. 

Anybody knows any reasonable graphic Cards which are supported ?

The bugs are everywhere and I don't have any problem with that but what really pissing me of is the fact that the problem known for 2 year minimum and not only therte is a solution ( I realize it might depend on Nvidia which might not give a particular damn on Ubuntu/Linux) but NOTHING from Ubuntu side even to trace the problem.

With all my disssatisfaction and critics of Windows/Microsoft they dide take care of problems.
Now I simply cfan't use my system since I need to go thru this "none" revertion 5 times during last half an hour. 
Sick of that !

---

### Post by supershin on 2010-09-18
Dunno why it isn't fixed but why don't you just leave it set to none for now. Or you could try reinstalling a older ubuntu distro, like hardy. That's a last resort thing though.

---

### Post by sl789 on 2010-09-18
Supershin , leaving to "none" is sucks because there is no border, windows has starnge pacement (conceal upper panel and because there is no border it's hard to move it.

Meanwhile I discovered something else : I choose KD and not Gnome as an option when I login and aboveformented problem doesn't happen under KDE. May be I am not using all the KDE options so it doesn't show up, but at least windows have normal borders and movable. Well may be I should stick with KDE, nobody died from it yet :-)

So now I even don't know if it's Gnome Xorg Nvidia or my card problem or all together

---

### Post by Rasa1111 on 2010-09-18
selecting "none" does nothing of the sort to my windows or borders. 

If "visual effects" is an issue, (like it is on my 7 year old PC)
its pretty logical, and easy.. to simply just not use it. 

 i know, i know..
then there wont be any "bling" to show off "cool effects". :lol:

 tis useless.

---

### Post by sl789 on 2010-09-18
Rasa1111, I can't care less for "special" effects. I assume that my driver/Gnome/Ubuntu/4 year old Dell has more severe problems than yours since that is effect of reverting to none on MY computer. Make a serach and you'll see that other people experience this as well. As I alsom mentioned sometimes it goes for hours and days with no single problem, sometimes it happens each 5 min. I switched to KDE this morning - no problems at all.
so it's most likely not my PC. 

It's certainly well-known problem, based on Googling it and it's a shame that it's not fixed so far. But I didn't pay for Ubuntu it's free software and I have to choice to use it or lose it. Notwithstanding it's annoing like hell since I get grat run with jaunty, hardy etc. My impression that with each new version Ubuntu gets a little less stable and required more time investment to get it run. Few years ago when I switch to it, everything run from the beginning, to my amasement. It's not the situation now, and it's especially profound with 10.04 ( 9.04 was quite good from the start as far as I can remember)

---

### Post by Rasa1111 on 2010-09-18
> But I didn't pay for Ubuntu it's free software and I have to choice to use it or lose it.

 well it's good to see you have your "head on straight" anyway. 
If only half of the people who came here complaining about this or that not working, and what a 'disgrace' it is, remembered that simple little fact,
it would be much more pleasant. lol

 I am rather new to Ubuntu though, 
only been using it 9-10 months, 
have used versions 9.10, 10.04, and 10.10 now, 
and all are very stable, and work amazingly great for me! 
(on this 7-8 year old dell dimension 2350!)
10.04 did give me a couple issues though, 
that were worked out shortly after..
but after that its been fantastic.

Sorry youre having issues mate.

---

### Post by sl789 on 2010-09-25
I am not sure it's going to help others, but I've found a recommendation that solved problem[B] in my case:
[/B]
see the link below for details

[http://magazine.redhat.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/](http://magazine.redhat.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/)


in /etc/X11/xorg.conf under 

Section "Device" for Nvidia card I added

Option "UseEvents" "on"

---

