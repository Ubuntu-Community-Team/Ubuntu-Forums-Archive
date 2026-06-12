---
title: "Increasing Computer Performance"
date: 2011-06-27
forum: General Help
---

### Post by Rog 3236 on 2011-06-27
[SIZE=2]My neighbor has a vintage Gateway computer. Processor speed less than 500Mhz, 256MB maximum RAM, 20GB hard drive. Unfortunately, she does not have the financial means to upgrade to another computer at this time. I did replace a Windows XP Home edition on it with Xubuntu as the sole operating system.[/SIZE]
 [SIZE=2]
[/SIZE]
 [SIZE=2]What I am looking for is some ideas of how I can get max performance out of the machine with the limited resources it has, particularly Internet speed. ( I have installed Chrome as a browser for that reason). I might also add she is not all that familiar with computers.[/SIZE]
 [SIZE=2]
[/SIZE]
 [SIZE=2]Any ideas would be appreciated.[/SIZE]
 [SIZE=3]
[/SIZE]

---

### Post by papibe on 2011-06-27
I think lubuntu could use less resources than Xubuntu.

Just a thought.

---

### Post by Ozymandias_117 on 2011-06-28
Honestly, I would start with a minimal install disk, or possibly even use a different Distro.  
Side note: Internet speed will be mainly limited by bandwidth and the speed of the ethernet card (Or modem if using Dial-Up); updating the operating system won't change those.

---

### Post by keithpeter on 2011-06-28
> **Rog 3236 said:**
> Any ideas would be appreciated.

Is this a desktop PC (I imagine it is)?

What is the system used for? Web and email? Writing and printing? Music? Photos?

How does it connect to the Internet? Wired router or usb modem or wifi?

Some tweaking of the Xubuntu startup applications may be possible based on the answers, and these may result in more RAM for applications.

I'd also suggest trying the Debian XFCE based live CD,I found it used less RAM when I tried it compared to Xubuntu, but still easy to use.

---

### Post by d3v1150m471c on 2011-06-28
[crunchbang!]("http://crunchbanglinux.org/") :)

You might also want to check out lxpanel. lightweight, highly configurable, stable panel.

---

### Post by keithpeter on 2011-06-28
Hello papibe and d3v1150m471c

If *I* had to use a machine with the specs mentioned by the original poster, I'd certainly be looking at Lubuntu, then AntiX Linux then Crunchbang.

However the op has mentioned that the lady who uses the target machine is not too cool with computers. Hence the interest in XFCE with its vaguely windows like arrangement and lack of CLI.

Any views?

What I think we need is a bomb proof IceWM based distro or similar that can run on a wired mains powered PC with minimal specs (P2 or P3, 128Mb ram). Such a distro would save so much landfill it would be untrue and it could enfranchise so many people...

---

### Post by snowpine on 2011-06-29
Software (such as a Linux operating system) cannot improve the performance of your computer or the speed of your internet connection.

What you can do is use the minimal software configuration necessary for the task at hand. This will use less resources (giving the impression of a faster computer) and require downloading less software/updates (which is good if you have a slow internet connection).

I have a system with similar hardware specs, and no Linux distro has ever made it perform like speedy modern hardware! That being said, for basic tasks, I've had excellent results with several distros including Xubuntu, CrunchBang, AntiX, Puppy, and SliTaz.

Frankly there are so many little things you can do to "streamline" the computing experience. For example, installing a Flash-blocking browser plugin; Flash video is a huge bandwidth hog and won't even play well on that computer anyway. It comes down to a question of how much time/effort are you willing to devote to helping your neighbor, and what are her expectations/needs for this hardware? Frankly (not to be critical) I think you possibly did her a disservice by removing Windows, because XP is known to run well on those hardware specs and unless you omitted something from your post, she does not sound like an experienced Linux user?

---

### Post by kaldor on 2011-06-29
Some people will probably hate me saying this, but try running the old LTS of Ubuntu. Ubuntu 8.04 or Xubuntu 8.04 might use a lot fewer resources than the modern stuff.

---

### Post by KoolPenguin on 2011-06-29
I agree with 'snowpine' that you probably should of left Windows XP on it, it does run very well with those older computers. I tried it myself with an older Netvista for the kids and put XP back on it as it ran faster and was more compatible/reliable with the hardware.

I suggest to try XP again, remove the apps she doesn't need to free up some HD space and possibly resources and install Google Chrome on it.

--
Chris

---

### Post by snowpine on 2011-06-29
> **kaldor said:**
> Some people will probably hate me saying this, but try running the old LTS of Ubuntu. Ubuntu 8.04 or Xubuntu 8.04 might use a lot fewer resources than the modern stuff.

I don't hate you! :)
But I do think it's bad advice... 8.04 has reached its "end of life" and therefore you can't install new apps from the Software Center (or whatever it used to be called). You don't want this first-timer to miss out on the thousands of awesome open-source applications just a few mouse clicks away! When I first discovered Ubuntu, browsing through the repos and installing new apps, games, etc. was a big part of the fun.

Not to mention the lack of security updates, bug fixes, and support on these forums.

Which brings up a good point: One of the best things you could do for this new user is put a shortcut to the Ubuntu Forums on the desktop and encourage her to sign up and post here with questions/problems! :)

---

### Post by Monotoko on 2011-06-29
> **kaldor said:**
> Some people will probably hate me saying this, but try running the old LTS of Ubuntu. Ubuntu 8.04 or Xubuntu 8.04 might use a lot fewer resources than the modern stuff.

I don't hate you either! I even have some old desktops with 8.04 that I couldn't upgrade, but I never connect them to the internet.

internet + out of support distro = Bad Idea™

---

### Post by grahammechanical on 2011-06-29
Based on my experience with using (until a few years ago) a machine with a lower specification than that machine, I would say that the time taken for a web page to download is very much dependent on how much memory is on the graphics adapter and also the speed of its GPU. 

Because of the lady's financial situation I would suggest that she consider upgrading her Patience. The only way to overcome the limitations of hardware is to change the hardware. I have a much better Internet experience now that I have a much more powerful computer.

Regards.

---

### Post by iposner on 2012-01-26
Putting XP back on any machine is a bad idea. As the other poster said "internet + old distro = bad idea" - and the same's even more true for an out-of-support version of Windows.

---

### Post by TenPlus1 on 2012-01-26
Try installing Bodhi Linux as it is based on ubuntu and has a very light desktop manager called enlightenment (E17)...  This should work well on those specs

[http://bodhilinux.com/](http://bodhilinux.com/)

---

