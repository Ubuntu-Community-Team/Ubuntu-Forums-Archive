---
title: "Ubuntu slower than Windows"
date: 2011-09-27
forum: General Help
---

### Post by subehsharma on 2011-09-27
Hi Guys,

With pain in my heart, i've to say that my little stint with Ubuntu has finally come to an end and i'm forced to move back to Windows. The reason is Ubuntu has been sluggish than Windows for some mysterious reasons. It was fast in the begining when i installed it but within a time span of 1 month the speed of opening apps reduced and now i have compared my windows app opening time being lesser than Ubuntu so i have no option but to switch back to Windows :(

---

### Post by nothingspecial on 2011-09-27
Moved to Testimonials since there is no support question.

---

### Post by subehsharma on 2011-09-27
well maybe somebody could have provided their inputs on how to make it faster so that i can think of coming back on Ubuntu in future?

---

### Post by sanderd17 on 2011-09-27
Can you post your systems specs? CPU speed, amount of ram, type of graphical card?

---

### Post by nothingspecial on 2011-09-27
Moved to general help, since it was indeed a support question. :D

---

### Post by subehsharma on 2011-09-27
Thanks NothingSpecial! :p

I've attached a screen capture when of Ubuntu Tweak window showing my laptop's specs.

---

### Post by peakpc on 2011-09-27
If you are looking for something snappy and light, don't go back to windows. Try Lubuntu, Xbuntu or something new Like Bodhi Linux (based on Ubuntu).  Linux is not the problem just desktop bloat (assuming that everything in your ubuntu is running correctly). Consider it a challenge to learn more about what things are running on your desktop and if they are really needed.

---

### Post by Mark Phelps on 2011-09-27
Both Windows and Linix distros are installed in a "vanilla" fashion, both perform well on some hardware and poorly on others, and both need tuning to improve performance.

Basically it comes down to two issues:
1) How much time and effort you're willing to commit to "tune" performance in ANY OS
2) Whether the result is worth it.

If you see Ubuntu as a challenge, and are willing to commit major time and effort, you could very well end up with MUCH better performance than Windows.  

But, the choice is yours.

---

### Post by sanderd17 on 2011-09-27
Your specs are good enough.

There are a few possibilities why your computer could be slow.

[LIST]
[*]Your graphical card isn't well supported, in that case the CPU takes over the rendering. But a CPU isn't made for it and makes the image stutter while it still slows down other processes. Until there are better drivers, you should choose another window manager that doesn't use those effects. You can use Gnome without effects or very light window managers like LXDE (in Lubuntu).
[*]your HDD is too full. If you use ext4, it doesn't get fragmented like Windows' ntfs. This is because it uses a smart algorithm of file placing. But that algorithm works best if there is a lot of free space. Try to have 20% free space at each partition.
[*]you installed a lot of things that always keep running: web-server, ssh server, backup program ... be sure to only install the ones you need.
[/LIST]

---

### Post by subehsharma on 2011-09-27
> **peakpc said:**
> If you are looking for something snappy and light, don't go back to windows. Try Lubuntu, Xbuntu or something new Like Bodhi Linux (based on Ubuntu).  Linux is not the problem just desktop bloat (assuming that everything in your ubuntu is running correctly). Consider it a challenge to learn more about what things are running on your desktop and if they are really needed.

Thanks alot man..I played with Fluxbox and LXDE and finally settled in on LXDE. Its blasting fast!!:p

One think which is strange is that after i installed nvidia graphics driver and hoped to see unity, i can't!:(:( During login i select "ubuntu" from the drop down menu and then login but after login, i only see my wallpaper, no taskbar or unity interface appear. I log out then and login back with "Ubuntu Classic" and it works as expected. Why am i not seeing Unity??

---

### Post by Blasphemist on 2011-09-27
So you just added LXDE to your existing installation and it works "blazingly fast"? If so that would tell us some things about the slowdown. Would seem to be video resource related in some way. And when you just choose the ubuntu (unity) session it is now just the background? Is that issue new?

This is the third thread I've seen today with this issue, one with unity, one 11.04 gnome and one 10.04 gnome. I wonder about maybe a gnome or x issue.

---

### Post by subehsharma on 2011-09-28
> **Blasphemist said:**
> So you just added LXDE to your existing installation and it works "blazingly fast"? If so that would tell us some things about the slowdown. Would seem to be video resource related in some way. And when you just choose the ubuntu (unity) session it is now just the background? Is that issue new?

This is the third thread I've seen today with this issue, one with unity, one 11.04 gnome and one 10.04 gnome. I wonder about maybe a gnome or x issue.

Yea. I just installed LXDE and i could see drastic improvement in the speed. Somebody had replied to this post that i haven't installed graphic card software and it was true. I didn't do it because with the software installed i face problem in my second screen. Anyways, i installed the software and the speed in ubuntu classic does increase but it is no where compared what i am gettng in LXDE env.

And just to test, after the software installation i tried to login into Unity but all i see is my wallpaper with no taskbar or any icons or any button.

---

### Post by sanderd17 on 2011-09-28
Yea, LXDE is very fast (and battery friendly), but you don't have some nice visual things.

I do wondor why the unity bar is missing.

Can you install ccsm (compiz config settings manager) from the software center? You should have Unity related options there. 

Don't change too much in the ccsm. Most settings are useless since Unity and can break your unity desktop or even your gnome desktop. Only changing Unity settings can't hurt though.

---

### Post by subehsharma on 2011-09-28
> **sanderd17 said:**
> Yea, LXDE is very fast (and battery friendly), but you don't have some nice visual things.

I do wondor why the unity bar is missing.

Can you install ccsm (compiz config settings manager) from the software center? You should have Unity related options there. 

Don't change too much in the ccsm. Most settings are useless since Unity and can break your unity desktop or even your gnome desktop. Only changing Unity settings can't hurt though.

i have installed ccsm but don't see any option for Unity

---

### Post by sanderd17 on 2011-09-28
weird, normally you should see something like this icon: [http://abledaemon.net/blog/wp-content/uploads/2011/05/20110509_ccsm_unity_plugin.png](http://abledaemon.net/blog/wp-content/uploads/2011/05/20110509_ccsm_unity_plugin.png)

Maybe your Unity is broken now, reinstalling could help.

---

### Post by subehsharma on 2011-09-28
this is what i see in my ccm

---

### Post by subehsharma on 2011-09-28
I just installed "Unity 2d" and it is amazing..Gives you the same functionality as a unity 3d but is less resource consuming.

---

### Post by Gatemaze on 2011-09-29
> **subehsharma said:**
> I just installed "Unity 2d" and it is amazing..Gives you the same functionality as a unity 3d but is less resource consuming.

I see you figured it out in the end... I have a better specs laptop and unity3d was not for me either... unity2d seems to do the job quickly and fine enough...

---

### Post by subehsharma on 2011-09-29
> **Gatemaze said:**
> I see you figured it out in the end... I have a better specs laptop and unity3d was not for me either... unity2d seems to do the job quickly and fine enough...

Glad it worked for u as well..Though i'm facing a new problem i.e. in unity 2d my wine apps have stopped working. They just don't execute! Could u also check this behavior on ur system?

---

