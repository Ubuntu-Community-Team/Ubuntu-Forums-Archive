---
title: "Lots of bugs in 11.10 and 12.04"
date: 2012-04-12
forum: General Help
---

### Post by linkingeek on 2012-04-12
I have been facing random hangs while executing mplayer with coreavc through wine 1.4 my whole system hangs lot many times when a "Wine crash" occurs with an error message "Internal errors-invalid parameters ..." same have been reported by 12.04 users not only that many bugs have been filed still no issue have been resolved this is the main reason i am losing my interest of ubuntu because in recent years i have faced a lot of bug situations(once resolved, yet seen) which are hardly seen on other distros where other apps like wine are blamed for bugs instead distro itself causes the problem since same is not experienced on other distro but my main cause for using ubuntu is that my collection of repos are only available for ubuntu.
mplayer have been installed through "ripps" repositry which was working fine with older ubuntu versions.
_______________________________________________________________________-
system specs
HP netbook 210
atom n450
2gb ddr2
realtek wifi
IDT audio
syaptic touchpad
xserver xorg intel installed along with "intel microcode package"

---

### Post by anejo on 2012-04-12
I've been using 12.04 for a few weeks. Read... only started using Ubuntu a few weeks ago for the first time! I was a long time Mint user and you can be fortunate not to have been around version 12 when the new gnome3 shell was introduced. The Mint devs made extensions and then embarked on a shell fork called Cinnamon which with one particular release broke almost every Mint installation. I've never had has many bugs and broken installs all in one release and so many times in a two week period. Anyway. I for one am enjoying this experience. Faulty? Yes. Some bugs? Yes. But this 12.04 is way, way better to manage than and dare I add, more fun to work with than Mint 12.

---

### Post by jadtech on 2012-04-12
isn'nt WINE a windows emulator ? What does this have to do with ubuntu directly , I would think you are looking for correction maybe from the wrong place ..

it is programs that have to keep there package up with the OS not the other way around, 11.10 is nearing the end of support 12.04 is still in beta I would say its WINE development not  keeping up with  developments..

---

### Post by na5h on 2012-04-12
Wine is a compatibility layer, not an emulator. Some applications work great with Wine and some applications don't work at all. You can check how well a certain application has been reported to work (or not work) at the Wine Application Database:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

Anyway, the Ubuntu Software Center is full of great applications that run natively on Ubuntu...are you sure that you actually NEED the specific application that you are trying to run using Wine? Doesn't Mplayer have a native Linux version, btw?

---

### Post by cariboo on 2012-04-12
As far as I remember mplayer was written as a native Linux app, then ported to Windows, why the op is using the Windows version with Wine, is beyond me.

---

### Post by na5h on 2012-04-12
> **cariboo907 said:**
> As far as I remember mplayer was written as a native Linux app, then ported to Windows, why the op is using the Windows version with Wine, is beyond me.
That's what I thought too.

Personally, I would recommend VLC or Totem (Ubuntu's default player).

---

### Post by jadtech on 2012-04-12
MY point was just this Ubuntu is an operating system, It is not programed and ported to the applications,  the applications are written and ported to and for it..

The fact that you would say WINE is not A emulator is silliness it is just that , the funnier part is just this  WINE makes a claim it can make windows run on Linux yet it can make WINE work on Linux  and then people come complain to this group ..

i really don't  like or want to say something wrong about any group but pointed out mplayer is native to Linux or was and ported to windows yet  apparently  wont do a good job  either way ya have to ask why anyone is interested in using it ..

---

### Post by na5h on 2012-04-12
> **jadtech said:**
> 
The fact that you would say WINE is not A emulator is silliness it is just that , the funnier part is just this  WINE makes a claim it can make windows run on Linux yet it can make WINE work on Linux  and then people come complain to this group ..

Well...there's been plenty of discussions and opinions regarding whether Wine is actually an emulator or not...my point being: Wine is not the kind of emulator you would think of when you hear the word "emulator". It's not an emulator in the same sense that [DOSBox]("http://www.dosbox.com/") or [DeSmuME]("http://www.desmume.com/") are.

As the [Wine Wiki FAQ]("http://wiki.winehq.org/FAQ#head-c9e6502ad636315e905d07f7e44594757a6738e3") states:
"When users think of an emulator, they tend to think of things like game console emulators or virtualization software. However, Wine is a compatibility layer - it runs Windows applications in much the same way Windows does. There is no inherent loss of speed due to "emulation" when using Wine, nor is there a need to open Wine before running your application. 
That said, Wine can be thought of as a Windows emulator in much the same way that Windows Vista can be thought of as a Windows XP emulator: both allow you to run the same applications by translating system calls in much the same way. Setting Wine to mimic Windows XP is not much different from setting Vista to launch an application in XP compatibility mode."

---

### Post by linkingeek on 2012-04-19
First of all corecodec is available on linux through wine and i have been already using it in earlier versions of wine now question arises if i use "coreavc" driver in mplayer, video plays(in crash it would might not have happened) but just "invalid parameter" dialog pops up and that's where my system hangs and continues until video is over and after that everything just become as normal.:confused:
___________________________________________________________________________
I am using native mplayer only and coreavc is on wine with native "dshowserver" compiled driver invoking "coreavc", to be used as an "-vo" option to mplayer.

---

### Post by sudodus on 2012-04-19
I don't know coreavc. What files are you playing (file codec, container ...)? If you let us know, maybe we can suggest a solution for you, that will work well!

---

### Post by na5h on 2012-04-20
Is it really necessary to use Wine for all this? If there is a native version (Linux-version) of mplayer available, why use Wine? Wine can often be troublesome, since it doesn't automatically "just work" with every available Windows app. 

According to what I've been able to find out just by googling around a bit, there should be no need to use Wine for coreavc with mplayer on Linux:
[http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)

Also, what type of files are your trying to play? A player like VLC or Totem might be able to play your files without any problems.

---

### Post by QIII on 2012-04-20
What Wine does or does not do well on a given distro is an objective fact, but not the failure of the distro.  If it doesn't work well in Ubuntu but does in another, by all means use the other.

Furthermore, WineHQ has a database of what Windows applications do and do not work well.  Different versions of the same software perform differently.

Finally, mplayer works natively in Linux.  If DirectX content (which is proprietary to Windows) does not play, then use Windows.

Otherwise, VDPAU (NVIDIA) and VAAPI with the XvBA back end (ATI) provide full hardware acceleration in VLC, mplayer and XBMC.

---

### Post by linkingeek on 2012-05-01
> **na5h said:**
> Is it really necessary to use Wine for all this? If there is a native version (Linux-version) of mplayer available, why use Wine? Wine can often be troublesome, since it doesn't automatically "just work" with every available Windows app. 

According to what I've been able to find out just by googling around a bit, there should be no need to use Wine for coreavc with mplayer on Linux:
[http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)

Also, what type of files are your trying to play? A player like VLC or Totem might be able to play your files without any problems.
Oh ho.. mplayer is native there is no offence regarding that but like you can have "dx9" as video output in mplayer (dx9 which is wine version of directx on linux)similarly "coreavc" also works on wine but produces its output on linux native "mplayer" which is done through "dshowserver"
Also, reason to use coravc is playback of h.264 in .mkv which is much faster on my netbook than any other codec or any netbook, some of you may suggest divx decoder w/o "looping" on HD content but still its lot slower on any atom based CPU.
There is slight confusion to whether wine is involved in this or not but if you see than i think "dshowserver" is wine dependent.

---

