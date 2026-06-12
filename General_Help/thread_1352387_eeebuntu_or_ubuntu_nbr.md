---
title: "eeebuntu or ubuntu nbr?"
date: 2009-12-11
forum: General Help
---

### Post by blur xc on 2009-12-11
My daughter is getting an Eee pc for christmas, and I will install some *buntu on it.  What does Eeebuntu do that Ubuntu NBR doesn't?  What about for non Eee pc netbooks- my wife is getting a Dell Mini as well, and will want Ubuntu on it.

thanks,
BM

---

### Post by joes7 on 2009-12-11
There is no major difference. I recommend Xubuntu. It is extremely easy to use, yet functional. It is great for newebies and experts.

---

### Post by pietro_spina on 2009-12-11
I have an eee 701 and I choose to run a regular Ubuntu installation with a couple of configuration changes.

Remove the bottom pannel
Replace the "Menu Bar" applet with the "Main Menu" one
Add the window list applet to the top bar
Add application shortcuts to the desktop for my faves...
       Empathy
       Chromium (browser)
       Home folder
       Anki
then I make the super key (on the 701 it looks like a house) be the shortcut for show desktop...

Oh and I've removed a ton of unneeded applications you may have different needs so I won't list them all but they include Open Office (replaced with AbiWord) and Gimp...

---

### Post by adaucourt on 2009-12-11
> **blur xc said:**
> My daughter is getting an Eee pc for christmas, and I will install some *buntu on it.  What does Eeebuntu do that Ubuntu NBR doesn't?  What about for non Eee pc netbooks- my wife is getting a Dell Mini as well, and will want Ubuntu on it.

thanks,
BM


for the dell mini you can use:
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

they are essentially the same as mentioned in a prior post except xubuntu is designed for low-specification computers.

> joes7 	 		**Re: eeebuntu or ubuntu nbr?**
 There is no major difference. I recommend Xubuntu. It is extremely easy to use, yet functional. It is great for newebies and experts. 

---

### Post by joes7 on 2009-12-11
> **adaucourt said:**
> for the dell mini you can use:
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

they are essentially the same as mentioned in a prior post except xubuntu is designed for low-specification computers.

Or people who want to save PC resources (like me):D

---

### Post by Inane_Asylum on 2009-12-11
For my eee 900, I'm using Cruncheee.  It's based off Ubuntu, has all the same repos, has a lightweight kernel, and uses openbox instead of metacity.  It works great for me...

---

### Post by t0p on 2009-12-11
I have an EeePC 701, and I run **Eeebuntu** on it.  Eeebuntu is basically normal Ubuntu, but with a custom kernel (called the Array.org kernel) and some scripts that ensure full hardware compatibility.  I use Eeebuntu 3, which is based on 9.04.  They haven't done the Karmic release yet.

Eeebuntu comes in 4 different forms:

[LIST]
[*]Standard (the classic Gnome desktop)
[*]NBR (with the Netbook Remix interface)
[*]Base (as Standard but with fewer applications installed by default - useful if you have limited disk space)
[*][LEFT]LXDE BETA (comes with the more minimalistic LXDE interface - useful if your EeePC has limited resources[/LEFT]
[/LIST]
You can get Eeebuntu [here]("http://eeebuntu.org/index.php?page=download").

[LEFT]As I mentioned above, the latest Eeebuntu 3 is based on Jaunty.  They haven't released a Karmic version yet.  But I'm not sure if a Karmic Eeebuntu is really necessary.  I've run a Karmic live usb on my EeePC 701 a couple of times, and hardware compatibility seems really good.  However, I haven't tested it properly yet.

If you don't mind using Jaunty, then Eeebuntu 3 is great.  If you really want to use Karmic, the regular Ubuntu may be the best choice. (Whether or not to use the NBR interface is a matter of personal preference: some users say the NBR interface is better for the small screen on the Eeebuntu; but I prefer the classic Gnome desktop.)  If you *do* decide to go with Karmic Ubuntu, it might be wise to look into installing the Array.org kernel.  Also look if there are ACPI scripts available for Karmic, to ensure hardware compatibility. 

**EDIT:**  According to some of the posters in [this thread]("http://forum.eeeuser.com/viewtopic.php?id=77957") on the EeeUser Forum, the vanilla Karmic kernel works fine with EeePC hardware, so the Array.org kernel is not required for running Karmic.  That isn't exactly what it says on [www.array.org]("http://www.array.org/ubuntu/"); but the fact remains that no Array.org kernel for Karmic has been released.  So vanilla Karmic might be fine for the EeePC.
[/LEFT]

---

### Post by blur xc on 2009-12-11
So many choices it makes my head hurt.  My wife isn't particularly interested in learning a lot of new things.  She likes what she's used to and is happy with that, so I think I'll stick w/ a normal Gnome setup.  My daugter is turning 5 (yeah, young to have her own computer, but that's a long story in itself), and sticking to somthing similar across the board for all of them is probably best.  My oldest boys are getting normal (cheap) laptops, and I'll set them up w/ dual boots.  If I'm counting right, 8 computers (laptops and netbooks) are being handed out this Christmas.  I think I'll have to change my title from Daddy to IT Manager.

Thanks for the input.  I think I'm probably going to go w/ the Karmic NBR- maybe....

BM

---

### Post by beetleman64 on 2009-12-11
It depends which eeePC it is. If its an original 701 model (Unlikely) then use eeebuntu, for a later model and for the Dell Mini or indeed any other netbook the use UNR.

---

### Post by pietro_spina on 2009-12-15
man with all that hardware to support I'd definitely invest in a couple honkin' big hard drives to store disk images of all those custom installs... 

Best of luck and where should I send my wish list? ;-)
-p

---

### Post by snowpine on 2009-12-15
"Regular" Gnome Ubuntu is a good place to start. You can see which hardware models are supported here: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)  (edit: I see this list is for 9.04.... sorry)

And of course, these forums are a good resource... definitely do a search on any specific model you're considering to learn the pros and cons (like Dell Mini wireless, which is an easily-solved problem in Karmic).

Ubuntu Netbook Remix is basically the same except for a "launcher" interface that people either love or hate.

While EEEbuntu was/is a fine project, I would not recommend installing it at the moment. They are in the process of switching the project over from Ubuntu to Debian, so if you install now, you're not guaranteed an upgrade path.

In my experience, unless it is my personal computer that I use every day and am willing to troubleshoot, I like to stick with the more "mainstream" distributions. Ubuntu, Debian, Fedora, etc. are all solid projects with lots of resources that aren't going anywhere any time soon. The small "remix" projects are hit-or-miss over the long term. For every success story like CrunchBang (great community and 2-year-plus track record!), there are multiple failed projects like Fluxbuntu or Eeexubuntu.

---

### Post by Carborundum on 2009-12-15
I'm using eeebuntu on my Eee PC 901, and it runs marvellously. Everything works literally out of the box. However, as stated eeebuntu 4.0 will be based on Debian Unstable rather than Ubuntu, due to some unfortunate occurrences of Ubuntu updates breaking things. I don't consider that a reason not to choose eeebuntu, but it's something to keep in mind.

---

