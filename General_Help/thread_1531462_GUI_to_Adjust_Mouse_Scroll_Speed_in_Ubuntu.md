---
title: "GUI to Adjust Mouse Scroll Speed in Ubuntu"
date: 2010-07-15
forum: General Help
---

### Post by OregonTrail on 2010-07-15
Ubuntu developers, Gnome developers, GTK developers, this post is aimed directly at you.

Lack of scroll wheel speed control in Ubuntu is an extremely serious issue! Currently, "pressing" mouse button 4 or 5 will scroll any page up or down by about 3 lines. This is *much too slow* for many users.

I recently wiped my hard disk off all things Microsoft and switched to Ubuntu 10.4. In my previous operating system, there was a nice GUI for increasing the number of lines scrolled by the mouse wheel. Thinking this a trivial user input setting, I searched for a similar GUI in gnome to no avail. 

Take one moment to imagine my dismay. I am not hesitant to admit that I use the mouse extensively. Most modern web-surfers do. I am used to my mouse scrolling 12 lines per click, so that I can skim comments and threads such as this one in a few seconds. Currently, on Ubuntu, it takes me 10 to 15 seconds to scroll through some comment pages. 

Apparently, you do not know the luxury of scrolling 10 or more lines at once with the mouse wheel click, as one gets used to eying important information from a quick scroll-through of a page that has thousands of lines of text. Right now I feel like I'm being forced to use a low bicycle gear on the steepest of hills. It is frustrating, maddening, and quite inconvenient.

It is obvious that there is a system-wide variable that controls the number of lines to be scrolled, as I also experience this problem in the IDE that I use. All we want as Ubuntu users is the ability to change this variable, just to know where this value lies would be information enough.

Yes, this issue has been talked about since 2002.
It appears in this Ubuntu answers post: (which should not be marked as solved!)
[https://answers.launchpad.net/ubuntu/+question/9200]("https://answers.launchpad.net/ubuntu/+question/9200")

I am aware that there is a formal bug associated with this:
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/124440]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/124440")

There is even a very active Ubuntu brainstorm topic for this:
[http://brainstorm.ubuntu.com/item/3214/]("http://brainstorm.ubuntu.com/item/3214/")

I know that this can be fixed in Firefox, which can somehow magically override the system scrolling value. Do I use Firefox? NO! I use Chromium, and 100 other application that use scrollbars. The maddeningly slow scrolling throughout the operating system gives me that feeling of toy-OS that I had when I first tried Ubuntu five years ago. 

Now I love everything about this distro, save for this one extremely aggravating and laughable oversight in user input customization. Is this not an accessibility issue? If I only had the use of the fingers on one hand, I would not want to waste hours of my life scrolling through pages that could take me three seconds to scroll. Not all disabled individuals have special input devices, they don't want to spend their life scrolling.

And don't tell me I can fix it in xorg.conf either, because if you mention "VertScrollDelta" it's is a device specific option that does nothing for most people.

This is not a "Wishlist" bug!
This not something to be "Triage"d!
And it surely is not a "Papercut"!
 
For me, and many tens-of-thousands of users like me, this is a "Chop of One's Fingers With an Exacto-knife" bug. Until it is fixed. 

Honestly, how hard can it be? 5 Lines of code added to the mouse-settings dialog.

---

### Post by OregonTrail on 2010-07-16
If anyone has a solution for this please post.

---

### Post by jsuhr on 2010-07-27
I have been searching off and on for quite some time now, and spent hours the last few days looking for *anything* at this point to speed up my mouse wheel. I too would greatly appreciate it if something were done about this, and completely agree with OregonTrail.

---

### Post by jsuhr on 2010-07-30
Bump

---

### Post by jsuhr on 2010-08-02
I am a senior in computer science and this is my last (fingers crossed) year and probably one of my hardest. I have a few weeks before school starts and accordingly have some spare time before I will need to divert my attention to class. If anybody could point me in the right direction I would love to try my hand at some sort of solution. Just some basic info on where to start would be greatly appreciated. I know, Google is my friend, but I would rather not spend days or possibly weeks during the remaining portion of my summer vacation searching in vain. Once again, any information to point me in the right direction would be appreciated. 
Didn't mean to intrude on your post OregonTrail, but would really like to get some solution at least started.

---

### Post by emaN-resU on 2010-08-05
Wow, talk about crickets chirping. I just wanted to add my support for this function. I hope we get some love soon.

---

### Post by gainead on 2010-08-10
Go to Ubuntu Software center and add Pointing Devices. This GUI allows you to adjust ALL settings for every mouse connected to the system... including scrolling speed.

---

### Post by jsuhr on 2010-08-10
Thank you gainead, have you adjusted scroll speed and verified a change? I have played with this program before (installed through synaptic) and after changing every setting I am unable to notice any difference in scroll speed, even after verifying which button is my wheel. Just for fun, I intalled through the Software Center and experienced the same results. Can anybody else post results from their experience with this app?

---

### Post by Paulgirardin on 2010-08-10
This may or may not be of any help,but I just booted into XP (something I do very rarely) and found that when back in Lucid, the mouse scroll wheel was very high.(MS wireless mouse)
I rebooted into XP ,went to mouse in control panel and hit apply.Rebooted into Lucid and scroll speed was back to normal.

---

### Post by jsuhr on 2010-08-10
@Paulgirardin
I think your mouse may have inherited settings from XP then ratained them in Ubuntu, it's not uncommon for one OS to change a setting in a device and have it "carry over", even through reboots. If you could replicate the situation and then use "xev" to show if your mouse is to blame. Xev just shows mouse actions, can be launched by typing "xev", and can help us track down what's going on in your situation. I'm guessing that for every 1 click (wheel roll), your mouse is showing multiple clicks.

---

### Post by maxx11 on 2010-10-03
bump...

---

### Post by zeating on 2010-10-03
Bump 

I'm surprised something so easy to implement and something you would think would be easy to do is not here at all. My mouse wheel scrolls so slow it takes so long just to get from the top of this page to the bottom. Hope this gets solved soon

---

### Post by dinamic1 on 2010-10-04
this is really frustrating ! :mad:

---

### Post by dinamic1 on 2010-10-06
bump

---

### Post by stinkeye on 2010-10-06
wrong thread

---

### Post by CalaverX11 on 2010-11-01
Bumping and resurrecting this, because I would absolutely love to know how to tweak the scrolling speed on the Magic Mouse under Maverick.

---

### Post by DachaArh on 2010-11-23
bump..

---

### Post by horseatingweeds on 2010-11-29
I'm also interested in some kinds of solution here. I've got two systems, a new and an old one. The new one is running Ubuntu in a Virtual box and has a cord mouse. Its scroll is normal. 

The old computer, I just loaded Ubuntu on as a dual boot with Win xp. It's got Microsoft Wireless Laser mouse 5000. This setup is terrible. The scroll is not smooth and is too fast. I tried the solution mentioned earlier - the one about booting into Win xp and clicking apply under mouse settings. It did nothing I noticed. 

This mouse was finicky when I was using Window's regular mouse driver. Once I switched to the Wireless Laser Mouse 5000 driver, the mouse started working nicely, smooth scroll. I figure this must be a hardware thing with the mouse that the driver makes up for.

**Edit:** I tried a different mouse, a basic corded one, usb. It works a lot better. The scroll is reasonable. I understand everyone's frustration with the slow-scroll now... I've been reading, and it looks like Linux doesn't have smooth-scrolling - yet.

---

### Post by humina on 2010-12-04
no resolution on this yet :(

---

### Post by 002244 on 2010-12-10
bumb! >:-[

---

### Post by joeknoodle on 2010-12-29
Going on five years with Ubuntu/Gnome.  Going on five years trying to scroll to the bottom of a page without getting carpal tunnel syndrome.  To try to introduce someone to this otherwise terrific OS, and the first complaint is &quot;I'm getting old scrolling&quot; is a death-knell to adoption.  If Ubuntu/Gnome doesn't care, after many, many, many, many complaints and requests, I can only assume they are not serious about presenting a serious challenge to other OSes.  Yes, I've used every available method, from command line, to that utterly useless &quot;Pointers&quot; GUI, to setting it up in xorg or whatever.  I'll give it one final chance in Natty, and I'm through.  My time is too valuable to spend it trying to scroll more than a few lines at a time.

---

### Post by Uhuu on 2010-12-29
This is just sooo ridiculous not having this option in gui. I know two people, who just quit using it even before they really started to know ubuntu because of this.

---

### Post by 0949er on 2011-01-06
ok so the answer is still "no options as of now"?

---

### Post by makuab on 2011-01-08
bump, having the same problem

---

### Post by lunatico on 2011-01-19
I thought I was been stupid and to able to find where to change this... have spend a few of hours in Google and nothing... now I see this thread and at least know I'm not alone.
I really love Ubuntu but this is rediculous.

---

### Post by sf_basilix on 2011-01-24
I came across this thread similarly to what others have said. I cannot find a resolution and quite frankly it's disturbing that it's 6 months with no response.

---

### Post by craftyguy on 2011-02-08
Bumpity Bump

Since Canonical made it a priority a while back to make xorg.conf obsolete, seems like they would have accounted for GUI-fying ALL aspects.

---

### Post by Guillaumeb on 2011-03-03
Bump again the "pointing Devices" app does not work with my Arc mouse

---

### Post by pennstatebadboy on 2011-03-16
I, too, am frustrated in not having the ability to change the speed of the scroll wheel. Logitech MX 1100 here.

Maybe the solution is more complicated than it appears.

Also, unable to map the DPI buttons.

---

### Post by lithopsian on 2011-03-16
This is Linux guys.  Learn to type.  I'm not aware of any simple GUI you can add.  At least not one that works.  Doesn't KDE include one?  You can use the xset command to change your mouse speed quite effectively.  Play with it and then store the preferred setting in your autostart shell script.  I use:
```
xset m 5/3 0
```

---

### Post by jrd43 on 2011-03-25
Didn't know about xset.  That totally worked.  I entered ```
xset m 5 1
```More on xset at [http://www.computerhope.com/unix/uxset.htm](http://www.computerhope.com/unix/uxset.htm) 

Now, who knows how to control the scroll speed?

---

### Post by sailor420 on 2011-04-03
Adding my own bump to this. Incredibly frustrating, and I can't believe this hasn't been addressed anywhere...

---

### Post by synchro505 on 2011-04-11
+1 Bump for original question. 

Adding an adjustment slider in the Mouse Preferences control panel would be outstanding. (I'm shocked it does not already exist given how long users have been asking for this)

Is there no app, patch, script, command line entry, or anything to allow users to adjust the speed of their scroll wheels on their mice? (not just in Firefox, but system wide?)

I'm keeping my fingers crossed and hoping for a solution soon. Thanks.

---

### Post by Sam___D on 2011-05-29
BUMP
I'm going mad. You can't use xset m for scrolling speed, only for pointer speed. This is really frustating. Pointer settings doesn't recognize my mouse.

---

### Post by Shellboy on 2011-06-19
bumpity

---

### Post by MrAntonB on 2011-07-12
> **lithopsian said:**
> This is Linux guys.  Learn to type.  I'm not aware of any simple GUI you can add.  At least not one that works.  Doesn't KDE include one?  You can use the xset command to change your mouse speed quite effectively.  Play with it and then store the preferred setting in your autostart shell script.  I use:
```
xset m 5/3 0
```

This is linux guys, can't you read? Mouse **Scroll** Speed... :D

---

### Post by liquidmonkey on 2011-07-13
this is a dumb problem to have LINUX (UBUNTU) MAKERS.

please please please fix it.

---

### Post by armagedalbeebop on 2011-07-18
i don't really need a GUI, but this is a really big issue for me.

---

### Post by zakk69 on 2011-07-31
Once a year (lesser now) I have a look at Ubuntu to see if it became user-friendly, and today I add my name to the list of those who give up because I don't want to loose any more time to **fix the mouse wheel speed !!!!!**

---

### Post by Isaacgallegos on 2011-08-29
Omg... bump

---

### Post by fiddler63 on 2011-09-20
Bumpity bump

---

### Post by Mikkelhaas on 2011-09-24
I agree, this issue needs to be addressed.  It's a basic function for an operating system to adjust mouse scroll speed.  Or are we all missing something??

---

### Post by OuchOfDeath on 2011-10-13
This is fundamentally an issue with the GTK toolkit. The toolkit itself does not offer this functionality at all, so any program using the toolkit(such as all of GNOME) cannot change the mousewheel speed. The QT toolkit has offered this forever, and KDE has a simply option to change mousewheel scroll speed in the same place Windows does. 

There is a bug report filed about it in the GTK bug database. I don't remember its exact age, but I'm pretty sure it's at least 6 years old. I'm pretty sure the GTK devs are simply not interested in adding this feature.

---

### Post by Bucic on 2011-10-28
Bump! The 'wtf' kind of bump...
Vote! [https://bugs.launchpad.net/gtk/+bug/124440](https://bugs.launchpad.net/gtk/+bug/124440)

---

### Post by ibladesi on 2011-12-31
Yeahh... bump.. 

about to try this, its pretty old.. don't know if it works
[http://sourceforge.net/projects/imwheel/](http://sourceforge.net/projects/imwheel/)

---

### Post by dbzzx on 2012-03-16
Uhhm anyone have a solution yet? I have carpal tunnel and as much as I like Xbuntu I am unsure I can stand scrolling so much to get down pages...

Anyone know a linux OS thats light on system requirements and still looks nice? :confused: :confused: :confused:

---

### Post by Sepero on 2012-07-16
The best solutions to this problem seem to be using gpointing-device-settings
sudo apt-get install gpointing-device-settings
[http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)

or some hacks
[http://ubuntuforums.org/showpost.php?p=10406312#20](http://ubuntuforums.org/showpost.php?p=10406312#20)

---

