---
title: "Multiseat Ubuntu 12.04"
date: 2012-08-16
forum: General Help
---

### Post by camerongray on 2012-08-16
Hi,

I manage a group of 4 desktop computers for a local youth group.  The computers are really old and becoming unusable but our budget cannot stretch to replace them all.  Instead I have decided to use second hand parts to build a single server with a quad output graphics card and set up Ubuntu as a multiseat server.

Does anyone have any simple step-by-step instructions on how to do this.  I have looked around for a good tutorial but all the ones that I can find seem to be very complicated and based on older versions of Ubuntu.

How I want the completed system to work:
[LIST]
[*]There will be one PC (Probably around a Core 2 Duo with about 4gb RAM)
[*]There will be 4 monitors connected to one or two graphics cards
[*]There will be 4 keyboards and mice connected via a couple of PCI USB cards
[*]I would ideally like to be able to output sound for each station through different outputs on a multichannel sound card but could use USB sound cards if it would be easier.
[/LIST]

I'd like performance to be reasonably good but the system will not be pushed hard, it will only be used for a couple of hours a week to browse Facebook or watch YouTube videos.

My main requirement is that it should be easy to set up (for my sanity) and easy for people to use, the target users are young teenagers with no Linux experience who just want to browse the internet.

Your help would be greatly appreciated!

---

### Post by unevenflow on 2012-08-16
Hey, if the 4 old computers have more than 233 Mhz CPU and 128 &#924;&#914; RAM you could use them as clients to LTSP along with the server you'll build, only extra requirements will be 4 Gigabit(1000) network cards for the clients, 1 Gigabit switch + as many Cat6 ethernet cables you need to connect them, all these are quite cheap

for more info see here:
[http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project](http://en.wikipedia.org/wiki/Linux_Terminal_Server_Project)
and here:
[https://help.ubuntu.com/community/UbuntuLTSP/](https://help.ubuntu.com/community/UbuntuLTSP/)

---

### Post by camerongray on 2012-08-16
I did consider that but decided that it would be better to sell the existing systems to put the money towards the new server as well as to save some space as space in the computer area is very limited!

---

### Post by Lars Noodén on 2012-08-16
Some of the older versions of Ubuntu used to have a package which provided multi-seat but that seems to have been taken out.  

There is this page:

[http://www.linuxtoys.org/multiseat/multiseat.html](http://www.linuxtoys.org/multiseat/multiseat.html)

I think the only way now is going to follow something like that.

---

### Post by |Anthony| on 2012-09-24
I have a *mostly* working multiseat setup built on Xubuntu 12.04. It wasn't too difficult to get it sorted out, but the one thing missing is audio per seat. I am [still working]("http://ubuntuforums.org/showthread.php?t=2062245") on that and once it's completed I will update the [MultiseatX]("https://help.ubuntu.com/community/MultiseatX") page.

I can tell you that using a single gpu makes your journey much more complicated. This will involve using Xephyr which is basically an Xserver that runs inside an Xserver. A wonderful blog outlining the process can be found [here]("http://beforeafterx.blogspot.com/").

---

### Post by bastafidli on 2012-09-28
> **|Anthony| said:**
> I have a *mostly* working multiseat setup built on Xubuntu 12.04. It wasn't too difficult to get it sorted out, but the one thing missing is audio per seat. I am [still working]("http://ubuntuforums.org/showthread.php?t=2062245") on that and once it's completed I will update the [MultiseatX]("https://help.ubuntu.com/community/MultiseatX") page.

I can tell you that using a single gpu makes your journey much more complicated. This will involve using Xephyr which is basically an Xserver that runs inside an Xserver. A wonderful blog outlining the process can be found [here]("http://beforeafterx.blogspot.com/").

Look at my config files attached to the bottom of the multiseatx wiki page. It has all the changes necessary to make per seat audio working.

---

### Post by |Anthony| on 2012-10-02
> **bastafidli said:**
> Look at my config files attached to the  bottom of the multiseatx wiki page. It has all the changes necessary to  make per seat audio working.
Does your implementation follow the seat, or the user? That is to say,  do your users have to login at the same seat every time, or does it not  matter who logs on to a seat since the sound is tied to the seat, not  the user?

Also, it would be nice for you to explain your methods.  What is the purpose of each file and what do the specific settings  therein do?

Please consider providing your answer on the question i asked specifically regarding [multiseat and pulseaudio]("http://ubuntuforums.org/showthread.php?t=2062245")

---

### Post by blackangelpr on 2012-10-09
i had been thinking to try multi seat since my family oftem want to use the computers at night so i thought 
if alsa could be recall for each seat by assigning N+1 addresses or is this issue with sound had been fix already?

dont know if i explain my self just in case i am a newbie so dont shoot me :lolflag:  hope to get any information regarding multi seat and  12.04  i want to try it soon...


will be a nice learning project for me.

---

### Post by bmidgley on 2012-11-08
I'm very excited to have this finally work!

So I mostly followed bastafidli's xorg.conf. I use kdm and specify a full /dev/.../by-path/... for each mouse and keyboard.

My problem is if the usb hub gets bumped, I plug something in or take something out. The mouse typically stops working and won't work again until kdm is restarted. Is there a way to have X be better at reconnecting devices? Or could I use some kind of proxy server or another way to keep the input hooked up? This is so close but this will be a dealbreaker if the seats are going to keep going dead on me.

---

### Post by bmidgley on 2012-11-08
BTW, I've got two pcix nvidia cards in a board with nvidia onboard graphics. I have one more slot I'll put a card in if these last issues can be swept up. Quad-core amd, enough to keep up.

For the record, my config: [https://gist.github.com/4043690](https://gist.github.com/4043690)

---

### Post by syb3ria on 2012-11-11
Can anyone help me with newbie "howto" about multiseat in 12.10? I'm using unity with lightdm and single 9800GT card.

---

### Post by bmidgley on 2012-11-11
[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX) seems to be the best we have. It would be nice if it could be cleaned for 12.04+ and the udev configuration documented with an example. I followed this to mostly get it done with kdm starting a gnome session.

I suspect completely working with udev will get around the problem of input devices going dead until the next kdm restart. (It happens if unrelated usb devices are plugged in)

I've got a couple of low-end nvidia cards with hdmi on order. I think this will solve some audio device issues... usb audio has been flaky and audio over hdmi means less cable mess as well.

---

### Post by bmidgley on 2012-11-19
I also see a problem that the audio device selection appears to be global. 

So if you open "sound settings" from two different seats (logged in as different users), changing the output device on one seat takes effect on the other as well.

I followed the steps on the wiki [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX) to use a system-wide daemon. My users are in groups plugdev and pulse-access among others.

---

### Post by bmidgley on 2012-12-11
I expected switching from analog audio to the hdmi audio through my nvidia 8400s would clean up my setup, eliminate wires, etc. In theory it has, as long as after each boot I go into the pulse control panel hardware tab and change each hdmi audio adapter from the fourth "Digital Stereo (HDMI) Output" to the third one (??)

---

