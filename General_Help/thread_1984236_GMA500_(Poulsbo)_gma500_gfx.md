---
title: "GMA500 (Poulsbo) gma500_gfx"
date: 2012-05-21
forum: General Help
---

### Post by bodhi.zazen on 2012-05-21
Welcome to the new support thread for the GMA500 (Poulsbo) graphics card.

This card should now be working out of the box with the gma500_gfx driver and minimal user intervention.

The driver should work out of the box with a 3.3.4 or higher kernel.

Documentation should be kept on the Ubuntu wiki:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Keep in mind, the wiki is a community maintained page.

Please use Launchpad for bug reports.

[B][COLOR="DarkRed"]Note: This thread is NOT for discussing the depreciated EMGD driver. If you need support for the EMGD please contact Intel.

A separate EMGD thread can be created as soon as the [gma500 team](https://launchpad.net/gma500) provides stable packages and adequate documentation.[/COLOR][/B]

---

### Post by thermatk on 2012-05-21
I have made some progress with taking the linux 3.4 kernel from quantal quetzal repos to precise but not from mainline ppa... Now there is gma500_gfx in lsmod but it's not starting anyway :(
I just want a newer version that might be better as I know that since 3.2 gma500_gfx saw a lot of changes

---

### Post by bodhi.zazen on 2012-05-21
I can not discern your problem from your post. I can not even tell what kernel you are running on which version of Ubuntu.

You will have to be more specific and check your logs. If you are running a custom kernel or the mainline kernel you are going to have minimal support (3.4 is still in development).

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

> **The mainline kernels builds are produced for debugging purposes and therefore come with no support. Use them at your own risk.**

12.10 is in very early development, you should be using the ubuntu +1 forums for that and, if you are using things in development, file bug reports.

[http://ubuntuforums.org/forumdisplay.php?f=416](http://ubuntuforums.org/forumdisplay.php?f=416)

I've had no problems with a higher kernel in Fedora 17 (due out next week).

Personally I compile my own kernel from source.

[http://bodhizazen.net/Tutorials/kernel](http://bodhizazen.net/Tutorials/kernel)

Or use the libre kernel

[http://jxself.org/linux-libre/](http://jxself.org/linux-libre/)

---

### Post by bodhi.zazen on 2012-05-21
I downloaded Ubuntu 12.10 Quantal Quetzal, daily build.

It booted fine with no modifications to the default boot parameters.

See terminal / screenshot

So I was unable to replicate your problem.

---

### Post by cataclop on 2012-05-23
Hello,

I wondered if it where possible to use an icc profile with gma500_gfx : I didn't succeed to do so, neither with dispwin nor with system settings panel in Ubuntu.

As I was advised, I'm going to fill a bug report ; but if someone knows a solution, it'll be welcome !

Many Thanks.

---

### Post by godfazr on 2012-05-24
Just installed 3.3.5 kernel to 12.04 (via deb files). After booting to new kernel:
- boot up fine without splash;
- screen resolution is 1024x768, which is wrong and makes me think that driver is not enabled;
- backlight adjusting doesn't work (at least without adding options to grub);
- no OSD for functional keys (Fn+key).

Question - if I'll install 3.3.4 will it give better result?

---

### Post by bodhi.zazen on 2012-05-24
> **godfazr said:**
> Just installed 3.3.5 kernel to 12.04 (via deb files). After booting to new kernel:
- boot up fine without splash;
- screen resolution is 1024x768, which is wrong and makes me think that driver is not enabled;
- backlight adjusting doesn't work (at least without adding options to grub);
- no OSD for functional keys (Fn+key).

Question - if I'll install 3.3.4 will it give better result?

Function keys are unrelated to the graphics driver. Enabling those keys has to do with your BIOS. Google search your hardware.

To see what driver you are using, check the logs or 

```
lsmod | grep gma
```

---

### Post by thermatk on 2012-05-24
**godfazr**,ubuntu mainline has no gma500_gfx built in :( You should compile it with the module for yourself. That's what I'm trying to do atm

---

### Post by godfazr on 2012-05-24
> **bodhi.zazen said:**
> Function keys are unrelated to the graphics driver. Enabling those keys has to do with your BIOS. Google search your hardware.
Function keys do work, but OSD not displayed, e.g. when changing volume level etc. Plus brighness adjusted only after reboot (i.e. no reaction when trying to adjust, but once you reboot it's brighter/darker).
Isn't it related to graphics driver?
> **bodhi.zazen said:**
> 
```
lsmod | grep gma
```
Doesn't give any output.
> **thermatk said:**
> **godfazr**,ubuntu mainline has no gma500_gfx built in :sad: You should compile it with the module for yourself. That's what I'm trying to do atm
sad to hear it, considering that in stock kernel for 12.04 (3.2.0) it was built in.

---

### Post by bodhi.zazen on 2012-05-24
> **godfazr said:**
> Function keys do work, but OSD not displayed. Plus brighness adjusted only after reboot.
Isn't it related to graphics driver?

More likely related to BIOS then graphics driver, guess it depends. On my hardware I have to disable a kernel module, has nothing to do with the graphics driver.

You really need to do some research before you assume it is a problem with the gma500_gfx.

> Doesn't give any output.

sad to hear it, considering that in stock kernel for 12.04 (3.2.0) it was built in.

If there is no output then you are not using the gma500_gfx, it is built and working.

---

### Post by thermatk on 2012-05-24
> **bodhi.zazen said:**
> 
If there is no output then you are not using the gma500_gfx, it is built and working.

What dou you mean?
I have installed 3.4 from mainline as you know and there is just no module inside and it was booting me into 800x600 with vesa or something like that

---

### Post by bodhi.zazen on 2012-05-24
> **thermatk said:**
> What dou you mean?
I have installed 3.4 from mainline as you know and there is just no module inside and it was booting me into 800x600 with vesa or something like that

The mainline kernel you installed is maintained by the Ubuntu kernel team. It is intended for testing only.

The kernel team did not enable the gma500_gfx module in the kernel .config , so it is not enabled.

You need to file a bug report with the kernel team and ask them to enable the gma500_gfx for the mainline kernel build or build a custom kernel yourself.

IMO a better option is to test the 3.4 kernel wither on 12.10 or Fedora 17.

Keep in mind we do not support custom kernels.

> Building and using a custom kernel will make it **very difficult to get support for your system**.

While it is a learning experience to compile your own kernel, you will not be allowed to file bugs on the custom-built kernel (if you do, they will be Rejected without further explanation).

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

And

> The mainline kernels builds are produced for debugging purposes and therefore **come with no support**. Use them at your own risk.

So while you are free to build kernels and learn to do so, support is limited at best. If the kernel team is not offering support ...

I think you are better off filing a bug report.

Why are you trying to use the 3.4 kernel ? Why are your building a custom kernel ?

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by cataclop on 2012-05-24
> **thermatk said:**
> **godfazr**,ubuntu mainline has no gma500_gfx built in :( You should compile it with the module for yourself. That's what I'm trying to do atm

Hello,

On my computer, this works very fine (and faster) with 3.4 from Quantal. I followed these instructions :
[http://www.upubuntu.com/2012/05/how-to-install-kernel-340-stable-on.html](http://www.upubuntu.com/2012/05/how-to-install-kernel-340-stable-on.html)

N.B : just after that, I removed Quantal lines from my sources.list to avoid unwanted updates… I think it would be possible to tune apt preferences, but I don't think all that is really supported.

Hope this will help.

---

### Post by thermatk on 2012-05-25
Nice day!
I have finally achieved success in installing Quantal kernel too and another problem I want to solve now is that the backlight brightness on my t91mt is still not easy to change.
There are some script workarounds but what about a hardcoded variant?
I have rebuilt gsd-backlight-helper with hardcoded psb-bl and it's really working!!!
So, for those who are fed up with all these scripts and console brightness...
download the file, unzip it and move the program with something like
```
sudo cp gsd-backlight-helper /usr/lib/gnome-settings-daemon
```
It will be immidiately available for changing brightness and make you happy :guitar:

---

### Post by thermatk on 2012-05-26
Hi!
Have you suspend working under 3.4? For me there is a regression in this kernel...

---

### Post by thermatk on 2012-05-26
An explanation for my workaround to make backlight be set natively with the keys:
Get the sources of gnome-settings-daemon:
```
apt-get source gnome-settings-daemon
```
It's probably in your home folder, go there and in plugins/power you will find gsd-backlight-helper.c.
That's the file that should be edited, so open it with gedit and you will see c-code.
There are two functions which should give the program path to the backlight changer. I can't fix them to work properly for everyone as I don't know C/C++ but i was able to replace them with simply a return to the needed psb-bl, which is enough for all the users of gma500 who have the problem. 
Than, compilation as usual and the only file we need is the one I provided previously that should be placed in the folder with actually working gsd.
If anyone knows what to do with these functions to make a proper fix which can be uploaded as a patch, that would be better... but for now it's enough to replace it once and fel like everything is fixed.
Original code:
```
static gchar *
gsd_backlight_helper_get_type (GList *devices, const gchar *type)
{
	const gchar *type_tmp;
	GList *d;

	for (d = devices; d != NULL; d = d->next) {
		type_tmp = g_udev_device_get_sysfs_attr (d->data, "type");
		if (g_strcmp0 (type_tmp, type) == 0)
			return g_strdup (g_udev_device_get_sysfs_path (d->data));
	}
	return NULL;
}

static gchar *
gsd_backlight_helper_get_best_backlight ()
{
	gchar *path = NULL;
	GList *devices;
	GUdevClient *client;

	client = g_udev_client_new (NULL);
	devices = g_udev_client_query_by_subsystem (client, "backlight");
	if (devices == NULL) {
		g_warning ("failed to find any devices");
		goto out;
	}

	/* search the backlight devices and prefer the types:
	 * firmware -> platform -> raw */
	path = gsd_backlight_helper_get_type (devices, "firmware");
	if (path != NULL)
		goto out;
	path = gsd_backlight_helper_get_type (devices, "platform");
	if (path != NULL)
		goto out;
	path = gsd_backlight_helper_get_type (devices, "raw");
	if (path != NULL)
		goto out;
out:
	g_object_unref (client);
	g_list_foreach (devices, (GFunc) g_object_unref, NULL);
	g_list_free (devices);
	return path;
}

```

---

### Post by cataclop on 2012-05-26
> **thermatk said:**
> Hi!
Have you suspend working under 3.4? For me there is a regression in this kernel...

In my case, I didn't ever have suspend working…

---

### Post by thermatk on 2012-05-26
Hmm, when I choose 3.2.0 to boot it suspends with the fix about quirk-vbemode-restore
But with 3.4 it's just hanging with black screen and bright backlight and won't go suspend... and even resume from this state

---

### Post by antonsky on 2012-05-27
hi i am using a sony vaio vpc-p
my backlight/display is 70% of the time flickering
resolution is 1600x768
i dont know if its backlight or the pixels, but changing of brightness doesnt affect flickering.
if you get close enough you can see diagonale lines on bright areas.
i am not sure if they are related to the flickering.
i am using ubuntu 12.04

it is extremely hard to find information for my laptop

---

### Post by sciurus on 2012-05-28
I wanted to report the state of my Sony Vaio P series VGN-P788K. I tested with a 12.04 32-bit install with all updates as of 2012-05-28 applied. The kernels used were 3.2.0-24 from precise and 3.4.0-3 from quantal.

**Graphics**
[LIST]
[*] 3.2: Boots to black screen. Switching to another tty then back to tty7 brings up graphics. They are always broken; only the upper half of the screen is used.
[*] 3.2 with console=tty1: Switching to another tty then back to tty7 brings up graphics. They are usually correct, but sometimes only the left two-thirds of the screen is used.
[*] 3.4: Switching to another tty then back to tty7 brings up graphics. They are always correct.
[*] 3.4 with console=tty1: No different than 3.4 without this option.
[/LIST]

**Suspend and Resume**

[LIST]
[*]3.2: Suspend and resume work out of the box.
[*]3.4: Suspend does not work. Although the screen goes blank, the laptop never suspends. I tried all the possible quirk options to pm-suspend but none changed this behavior.
[/LIST]

---

### Post by bodhi.zazen on 2012-05-28
> **sciurus said:**
> I wanted to report the state of my Sony Vaio P series VGN-P788K. I tested with a 12.04 32-bit install with all updates as of 2012-05-28 applied. The kernels used were 3.2.0-24 from precise and 3.4.0-3 from quantal.

**Graphics**
[LIST]
[*] 3.2: Boots to black screen. Switching to another tty then back to tty7 brings up graphics. They are always broken; only the upper half of the screen is used.
[*] 3.2 with console=tty1: Switching to another tty then back to tty7 brings up graphics. They are usually correct, but sometimes only the left two-thirds of the screen is used.
[*] 3.4: Switching to another tty then back to tty7 brings up graphics. They are always correct.
[*] 3.4 with console=tty1: No different than 3.4 without this option.
[/LIST]

**Suspend and Resume**

[LIST]
[*]3.2: Suspend and resume work out of the box.
[*]3.4: Suspend does not work. Although the screen goes blank, the laptop never suspends. I tried all the possible quirk options to pm-suspend but none changed this behavior.
[/LIST]

You probably want to file bug reports on that behavior. I can not repeat you black screen / distortion problem and the suspend issues sounds like a regression.

---

### Post by thermatk on 2012-05-29
> **sciurus said:**
> 

3.4: Switching to another tty then back to tty7 brings up graphics. They are always correct.
...
3.4: Suspend does not work. Although the screen goes blank, the laptop never suspends. I tried all the possible quirk options to pm-suspend but none changed this behavior.

The first problem can be beaten with some workarounds like disabling plymouth and changing the resolution in grub and i915-connected files.

The second is a regression, I have the same problem, wrote about it in my previous post... Someone can post a bug at kernel.org as i don't feel like i understand how to do this and i have the skills

---

### Post by godfazr on 2012-05-29
> **sciurus said:**
> Switching to another tty then back to tty7 brings up graphics. They are always correct.
Remove "splash" from boot options, for me that helped on 3.2.0 and 3.3.5.

---

### Post by mozphere on 2012-05-30
I also have an Acer A0751h and the boot options bodhi.zazen  suggested worked great. However, I have some questions regarding performance.

I can't watch videos online because sometimes the video and sound get out of sync, the video freezes, and things like that.
Are you able to watch videos? If so, what other configurations changes have you made?

Have you tried programming on this computer?

I'm just trying to get the best performance possible because even Gmail takes a little to long to load...

Thanks

---

### Post by mikewhatever on 2012-05-31
> **mozphere said:**
> I also have an Acer A0751h and the boot options bodhi.zazen  suggested worked great. However, I have some questions regarding performance.

I can't watch videos online because sometimes the video and sound get out of sync, the video freezes, and things like that.
Are you able to watch videos? If so, what other configurations changes have you made?

Have you tried programming on this computer?

I'm just trying to get the best performance possible because even Gmail takes a little to long to load...

Thanks

Watching online video (in browser) doesn't work very well in 12.04. In fact, anything related to multimedia or to rendering heavy web content would greatly benefit from hardware acceleration, which the combination of gma500 and psb_gfx lacks completely.
Programming shouldn't pose a performance problem, unless you'll be compiling something the size of the Linux kernel. It's mostly just plain text, and if you are happy with the screen real estate, by all means, try it.

---

### Post by sebastiansu on 2012-06-01
Hallo,

can the GMA500_gfx module control multi displays with different resolutions?

---

### Post by thermatk on 2012-06-01
**mozphere,mikewhatever,**
Videos from Youtube are working on 360p and more with flashvideoreplacer and mplayer
with flash it's crap
and without mplayer it's buggy
should I explain this easy modifications?

---

### Post by docpark on 2012-06-02
Just loaded the latest Ubuntu 12.04 to my late model Sony Vaio P-Series microlaptop (VPCP11SKX) which has the Intel GMA500 onboard graphics. When I trialed the OS from the USB stick, it booted up well and everything seemed to work. On installing, the problem is the screen.

At first, it booted up to a black screen after intially showing the splash screen. By pressing F1 during boot, it would then randomly boot to different screen sizes or to the correct screen resolution ( 1600x768 ) but using only half the screen. 

I figured out that by logging out and logging in when only half the screen resolution came up that it would come out using the whole screen, as in the trial. 

When I look at system details, it tells me the Graphics are "unknown"

How do I load the gma500 driver and will that fix my screen problem

---

### Post by bodhi.zazen on 2012-06-02
> **docpark said:**
> How do I load the gma500 driver and will that fix my screen problem

Did you not read the first post ?

See : [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

Is there some step on the wiki page you did not understand ?

---

### Post by badook on 2012-06-03
I know this is a little off topic but....Thank you Alan Cox for developing this driver!

---

### Post by Mehdiing on 2012-06-04
Hi,

I have installed psb-gfx for Ubuntu 11.10. How can I générate the config file? For Emgd for example it is possible with the command 
```
sudo emgd-xorg-conf
```
it generate 10-emgd.conf file into /usr/share/X11/xorg.conf.d. How can-I do the same with psb-gfx and gma-gfx for ubuntu 12.04?

Thanks.

---

### Post by bodhi.zazen on 2012-06-04
> **Mehdiing said:**
> Hi,

I have installed psb-gfx for Ubuntu 11.10. How can I générate the config file? For Emgd for example it is possible with the command 
```
sudo emgd-xorg-conf
```
it generate 10-emgd.conf file into /usr/share/X11/xorg.conf.d. How can-I do the same with psb-gfx and gma-gfx for ubuntu 12.04?

Thanks.

What kernel are you using ? You do not need an xorg.conf for the gma500_gfx

---

### Post by Mehdiing on 2012-06-04
> **bodhi.zazen said:**
> What kernel are you using ? You do not need an xorg.conf for the gma500_gfx

Thanks for replying,
I'm using [FONT=monospace]mainline kernel [/FONT]3.4.0-999 for ubuntu 12.04 and 3.0.0.20 for ubuntu 11.10.
I need this file to install the eGalaxTouch drivers.

---

### Post by Sakartu on 2012-06-19
Hey all,

I was wondering.. what do you guys use to watch a decent avi/mkv these days? I tried a few, but none really work flawlessly... I know there is no hardware acceleration, but still.

Cheers,
Sakartu

---

### Post by mikewhatever on 2012-06-20
> **Sakartu said:**
> Hey all,

I was wondering.. what do you guys use to watch a decent avi/mkv these days? I tried a few, but none really work flawlessly... I know there is no hardware acceleration, but still.

Cheers,
Sakartu

I still use Lucid with the old (2008) psb driver.

---

### Post by jherskow on 2012-06-20
Ok, i heard about the new support for gma500, and decided to do a fresh install of 12.04
on my old, nearly untouched AAO 751h.
when booting from the live cd, i took a forum members advice and did something like restart lightdm. (i am a very un-savvy user. i can follow instructions to use the terminal and change things, but i usually won't understand what i'm doing.)
now when i boot up i get a black screen, which i can overcome somewhat by plugging in an external monitor.

I'm finding myself rather confused about where to go from here, do i need to do all these settings changes i see written everywhere? or do i just need to run update manager to get the new kernel that supports gma500.

I'd really appreciate it if someone could help me out here :).

---

### Post by jherskow on 2012-06-20
ok, ran update manager and it still boots blank.

---

### Post by prince_of_darkness on 2012-06-20
> **Sakartu said:**
> Hey all,

I was wondering.. what do you guys use to watch a decent avi/mkv these days? I tried a few, but none really work flawlessly... I know there is no hardware acceleration, but still.

Cheers,
Sakartu

I don't use Linux (ubuntu) to watch any videos. I use Windows 7 for all my multimedia needs, much better performance. Just keep Ubuntu as a backup to see how the development is going. Sorry i can't be more help

---

### Post by prince_of_darkness on 2012-06-20
> **jherskow said:**
> Ok, i heard about the new support for gma500, and decided to do a fresh install of 12.04
on my old, nearly untouched AAO 751h.
when booting from the live cd, i took a forum members advice and did something like restart lightdm. (i am a very un-savvy user. i can follow instructions to use the terminal and change things, but i usually won't understand what i'm doing.)
now when i boot up i get a black screen, which i can overcome somewhat by plugging in an external monitor.

I'm finding myself rather confused about where to go from here, do i need to do all these settings changes i see written everywhere? or do i just need to run update manager to get the new kernel that supports gma500.

I'd really appreciate it if someone could help me out here :).

Follow the instructions here to fix the black screen problem [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo")

---

### Post by jherskow on 2012-06-20
id did that with the liveUSB, i am currently post install and instead of a half black screen, it is now completely black, and i'd like to know how to get it to function.

---

### Post by bodhi.zazen on 2012-06-20
> **jherskow said:**
> id did that with the liveUSB, i am currently post install and instead of a half black screen, it is now completely black, and i'd like to know how to get it to function.

What configuration changes did you make post-install ?

---

### Post by jherskow on 2012-06-20
No, as soon as I installed 12.04 I restarted the computer, and since then it's always a black screen. If I plug in an external monitor the external monitor stays black and the regular screen displays only left two thirds of the picture.

---

### Post by bodhi.zazen on 2012-06-20
Restart X as described on the wiki page.

Then make the post install configuration changes.

Alternately use Ubuntu 12.10 or Fedora 17, both have a more recent kernel and both will have X working out of the box.

All this is described on the wiki page you were given

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Live_.28Desktop.29_CD](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Live_.28Desktop.29_CD)

---

### Post by jherskow on 2012-06-24
Ok, i did the grub edit to tty1, but im still getting a completely blank screen.


-12.04 of an AAO 751h. fresh install.

---

### Post by bodhi.zazen on 2012-06-24
You are going to be more specific then that. What edit did you make exactly ? And did you you then update grub ?

---

### Post by godfazr on 2012-06-25
> **jherskow said:**
> Ok, i did the grub edit to tty1, but im still getting a completely blank screen.


-12.04 of an AAO 751h. fresh install.
Try next:
1. Press Ctrl+Alt+F1 then Ctrl+Alt+F7 to see desktop;
2. Remove "splash" from boot options (in same place where you're adding tty1);
3. Update grub.
That helped me with my AAO 751h.

---

### Post by jherskow on 2012-06-26
I'm not too savvy a user, could you explain what you mean by remove splash?
Does that mean removing the entire line, or just the word splash from that line?

Thanks

---

### Post by bodhi.zazen on 2012-06-26
> **jherskow said:**
> I'm not too savvy a user, could you explain what you mean by remove splash?
Does that mean removing the entire line, or just the word splash from that line?

Thanks

Just the word splash

FWIW - an updated kernel will not have this problem. The easy choices for an updated kernel would be to use Ubuntu 12.10 or Fedora 17.

Ubuntu 12.10 is in alpha, so may be buggy.
Fedora 17 looks stable, but gnome is slow, so use kde, xfce, or lxde spins.

The other option would be to install an updated kernel from backports.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by thermatk on 2012-06-26
Anyone knows what is this?
[http://people.freedesktop.org/~zhen/cedarview/](http://people.freedesktop.org/~zhen/cedarview/)
That thing could make us happy in addition to gma500_gfx

---

### Post by jherskow on 2012-06-26
Thanks! removing splash did the trick for me...

is there anything underway to enable 3d and hardware acceleration?

---

### Post by leorosa on 2012-06-28
Hi Fellows!

Does anyone here can tell me please if our gma500 on Precise is compatible with Redshift ([http://jonls.dk/redshift/](http://jonls.dk/redshift/))?

I realy would love to use this tool but it seems to not work for me...

Thanks in advance! :)

---

### Post by onebir on 2012-06-28
Been trying to get screen rotation working on the [accursed Asus T91](http://ubuntuforums.org/showthread.php?p=12059946#post12059946).

Are the problems I've had due to the ["extremely limited"](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#PSB-GFX_drivers) support? (ie it's a complete lost cause..?)

(I'm pretty sure this worked with drivers in Ubuntu 11.10 or so - but plenty other things didn't... )

---

### Post by mpw on 2012-06-30
Thanks to all developers here! With the updated Wikipage for the gma500 I finally managed to get suspend working on my Sony Vaio X Series! This makes a netbook a netbook - quick resume :) I'm so happy - thank you so much.

---

### Post by mikewhatever on 2012-06-30
> **mpw said:**
> Thanks to all developers here! With the updated Wikipage for the gma500 I finally managed to get suspend working on my Sony Vaio X Series! This makes a netbook a netbook - quick resume :) I'm so happy - thank you so much.

Glad it works for you. That said, I don't think that people here are developers. Anyway, the driver you use was made primarily by [Alan Cox]("https://en.wikipedia.org/wiki/Alan_Cox"). Ironically, he is employed by Intel, the company responsible for creating the gma500 driver mess.

---

### Post by onebir on 2012-06-30
Has anyone using the gma500_gfx done today's kernel upgrade?

I'm a bit leery of it given problems I've had getting a GMA500 netbook working recently...

---

### Post by gadgetfr34k on 2012-07-02
Hi Guys,
 
I have Dell Mini 1010 with GMA 500 chipset. I installed the Ubuntu 12.04 and followed instructions for dorting out sistorted display/blank screen.
 
I am stuck with the 1024x576 screen display now. 
 
The supported resolution for notebook is apparently 1366x768.
 
I have tried modifing the GRUB_GFXPAYLOAD_LINUX and GRUB_GFXMODE to 1366x768x32 ( as per wiki) but it is not resolving the issue.
 
Can you please suggest any alternatives to fix this thing ?
 
Thanks

---

### Post by bodhi.zazen on 2012-07-02
> **gadgetfr34k said:**
> Hi Guys,
 
I have Dell Mini 1010 with GMA 500 chipset. I installed the Ubuntu 12.04 and followed instructions for dorting out sistorted display/blank screen.
 
I am stuck with the 1024x576 screen display now. 
 
The supported resolution for notebook is apparently 1366x768.
 
I have tried modifing the GRUB_GFXPAYLOAD_LINUX and GRUB_GFXMODE to 1366x768x32 ( as per wiki) but it is not resolving the issue.
 
Can you please suggest any alternatives to fix this thing ?
 
Thanks

See [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Post_installation](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Post_installation)

---

### Post by gadgetfr34k on 2012-07-02
> **bodhi.zazen said:**
> See [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Post_installation](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/#Post_installation)
 
 
Hi bodhi,
 
I had went through the wiki, and tried creaing 01_915resolution file and the other GRUB_GFXMODE and GRUB_GFXPAYLOAD_LINUX parameters. (subsequently update-grub).
 
The resolution is still at 1024x576.

---

### Post by bodhi.zazen on 2012-07-02
> **gadgetfr34k said:**
> Hi bodhi,
 
I had went through the wiki, and tried creaing 01_915resolution file and the other GRUB_GFXMODE and GRUB_GFXPAYLOAD_LINUX parameters. (subsequently update-grub).
 
The resolution is still at 1024x576.

I use console=tty1 and revome the splash option.

If 195_resolution and GFXPAYLOAD are not working for you, try an alternate soltuion.

Also you will have better success with a newer kernel.

---

### Post by KarmicKarmicChameleon on 2012-07-04
> **gadgetfr34k said:**
> Hi Guys,
 
I have Dell Mini 1010 with GMA 500 chipset. I installed the Ubuntu 12.04 and followed instructions for dorting out sistorted display/blank screen.
 
I am stuck with the 1024x576 screen display now. 
 
The supported resolution for notebook is apparently 1366x768.
 
I have tried modifing the GRUB_GFXPAYLOAD_LINUX and GRUB_GFXMODE to 1366x768x32 ( as per wiki) but it is not resolving the issue.
 
Can you please suggest any alternatives to fix this thing ?
 
Thanks

I have the 1010 too. The max is 1024x576. It's the other Mini 10's (1012) that have 1366 displays. Even so with these screens the display is fantastic.

---

### Post by TakeLifeEasy on 2012-07-07
Hi,

I had Gnome 3 working on my Dell 1010 running 12.04 but now has stopped working, just goes into Gnome classic.

Anyone else running Gnome 3 on this chipset yet?

---

### Post by bodhi.zazen on 2012-07-09
> **TakeLifeEasy said:**
> Hi,

I had Gnome 3 working on my Dell 1010 running 12.04 but now has stopped working, just goes into Gnome classic.

Anyone else running Gnome 3 on this chipset yet?

Gnome3 works with llvmpipe, although it is slow.

I do not think llvmpipe has been fully ported to Ubuntu yet (used it on Fedora).

---

### Post by lucazade on 2012-07-10
gma500_gfx is currently broken in Quantal 12.10 and kernel 3.5.

here is a collection of patches:
[http://ubuntuforums.org/showthread.php?t=2012088&page=2](http://ubuntuforums.org/showthread.php?t=2012088&page=2)

.. if anyone want to make a dkms ppa or open a bug report for it..

---

### Post by Veaceslav on 2012-07-11
Hello I have an Asus 1101HA with gma 500 and recently installed Kubuntu 12.04

I had Kubuntu 11.04 until then with old driver that ate all my cpu.

Now current gfx_psb driver is doing s good job, ans system is much faster.

But brightness hot-keys doesn't work, and the most important thing, when moving over elements, mouse cursor flicker, or dissapear when pressing a button and after moving away will appear.

There is any way to configure gfx_psb driver or someone had the same problem with flickering cursor and know a workaround?

Thanks,

Veaceslav

---

### Post by gsedej on 2012-07-23
What's the situatin with kernel 3.5 final?

Is it possible to use some linux3.5 .deb (that includes gma500_gfx) with Ubuntu 12.04?

---

### Post by bodhi.zazen on 2012-07-23
> **gsedej said:**
> What's the situatin with kernel 3.5 final?

Is it possible to use some linux3.5 .deb (that includes gma500_gfx) with Ubuntu 12.04?

you can try installing a 12.10 kernel on 12.04 or compile your own.

See : [http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads](http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads)

Or try the -libre kernel

[http://jxself.org/linux-libre/](http://jxself.org/linux-libre/)

---

### Post by gsedej on 2012-07-24
Great. Is there any progress on this driver? are there some new features in kernel 3.2 vs 3.5 except bugfixes?

---

### Post by gaby81 on 2012-07-31
Greetings

I use gma500_gfx driver

I have two question
1. I try to launch xbmc, but it requires screen depth of 24 bit. Since I don't have any xorg.conf file where I can change it, how I can change the color depth?
2. Can you please advise the best video player for the gma500_gfx driver

Thanks

---

### Post by mikewhatever on 2012-08-04
> **gaby81 said:**
> Greetings

I use gma500_gfx driver

I have two question
1. I try to launch xbmc, but it requires screen depth of 24 bit. Since I don't have any xorg.conf file where I can change it, how I can change the color depth?
2. Can you please advise the best video player for the gma500_gfx driver

Thanks

1. The colour depth is usually 24 by default, so I rather doubt that's the problem. xbmc is probably not a good candidate for gma500 machines to start with, something like openbox is a better option. Anyway, you could try creating xorg.conf and setting whatever is needed there.
[http://superuser.com/questions/173123/how-to-change-the-color-depth-in-ubuntu-10-04](http://superuser.com/questions/173123/how-to-change-the-color-depth-in-ubuntu-10-04)

2. With no hardware acceleration, all video players are equally limited. In fact, I don't think a gma500 machine can be considered as multimedia hub at all. It's ok for coding, some internet, pictures and music, but not video.

---

### Post by gaby81 on 2012-08-05
Thanks Mike, but in fact, EMGD drivers - 1.10 and 1.14 are capable to handle 1080p with almost sleek experience. XMBC also shows pretty good performance with those drivers, so I think the problem is with the new drivers

---

### Post by mikewhatever on 2012-08-05
> **gaby81 said:**
> Thanks Mike, but in fact, EMGD drivers - 1.10 and 1.14 are capable to handle 1080p with almost sleek experience. XMBC also shows pretty good performance with those drivers, so I think the problem is with the new drivers

Yes, as said above, the new driver doesn't provide hardware acceleration, which is unlikely to change any time soon, but you are welcome to use whatever works best for you, especially if you know how to make that stuff work.

---

### Post by gaby81 on 2012-08-05
Do you know why Ubuntu has stopped their support for the EMGD driver and switched to the gma500_gfx? Till the last release those drivers worked pretty good comparing to the gma500_gfx

---

### Post by mikewhatever on 2012-08-05
> **gaby81 said:**
> Do you know why Ubuntu has stopped their support for the EMGD driver and switched to the gma500_gfx? Till the last release those drivers worked pretty good comparing to the gma500_gfx

Let's get some facts straight first:

1. Ubuntu devs have never provided support for EMGD. It's a closed source driver released by Intel, and never has it been the default one. That also means that there has been no switch from EMGD to gma500_gfx.

2. EMGD is not made for Ubuntu, and because of the way it is tied to the kernel and xserver versions, it doesn't work (in Ubuntu) without some major adjustments (xserver downgrade, etc). gma500_gfx, on the other hand is built in, and, though limited, works almost out of the box in Ubuntu and any other distro.

3. Some of the community members (aka gma500 team) were able to make EMGD work in older Ubuntu releases. That work is still available, and is free to use as you see fit. However, the efforts have proved unsustainable in the long run, and I do not know if they will be resumed. As far as I know, EMGD doesn't work at all in 12.04, so you are welcome to take up the job.

So, if you wish to use another driver, feel free to do that. Information on how to do it is available in the wiki. If you have further question regarding EMGD, post a new thread, otherwise, will drift off topic fast here.

---

### Post by merlinux4 on 2012-08-11
Hi everybody,

this is my first message on the forum!

I installed Xubuntu 12.04 on my Asus eeepc 1101HA (GMA500). I followed the post installation instructions on the [wiki page]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Live_.28Desktop.29_CD") and solved the black screen problem.

Now I have _two problems_:
**[COLOR="DarkRed"]1. [/COLOR]**Parole is not able to read .avi documents. Gives this message "Could not initialise Xv output". VLC doesn't work too.

**[COLOR="DarkRed"]2. [/COLOR]**I tried to fix the brightness hotkeys following the same wiki page; now they show a brightness icon in the middle of the screen but brightness doesn't change.

I don't know if this thread is the right one for my issues. 
I can follow instructions to use the terminal but often I don't know what I am doing.

Thanks!

---

### Post by runninglot on 2012-08-14
Hello

I am running 12.04. I have a few questions on gma500_gfx.
[LIST]
[*]To make X work again I had to do apply the 915resolution fix and delete the 10-emgd.conf file from /usr/share/X11/xorg.conf.d. However, if the other files in that folder are removed, keyboard and touchpad are disabled. That makes wonder if the file containing the traditional Device, Screen etc. section is needed. (bhodi.zazen wrote an xorg.conf is not needed, and that is basically what 10-emgd.conf is.)

[*]I am not sure I am using gma500_gfx. How do I tell? Using kernel 3.2.0 from the 12.04 distribution or v3.3.7-precise from the mainline repository, there is no gma500 in the output of lsmod. With kernel v3.5.1-quantal, lsmod returns several lines with gma500, however there is no noticeable difference.

[*]With all kernels, Gnome cannot load a background image on the desktop (after I've logged in).
[/LIST]

Can someone help me?

rl

---

### Post by bodhi.zazen on 2012-08-14
You have to remove the emgd driver and all associated files.

---

### Post by runninglot on 2012-08-14
They had been removed, (there are no packages matching 'emgd' in synaptics) and the 10-emgd.conf in /usr/share/X11/xorg.conf.d had also been renamed. Still the gma500 related modules are only shown as loaded when running v3.5.1-quantal, although the window system is fully operational.

Concerning the absence of a desktop wallpaper, may compiz have anything to do with it?

rl

---

### Post by bodhi.zazen on 2012-08-14
I do not think the absence of a background images is in any way related to the gma500_gfx driver.

---

### Post by runninglot on 2012-08-14
> **bodhi.zazen said:**
> I do not think the absence of a background images is in any way related to the gma500_gfx driver.

Thank you for your suggestion, which made it easier to find the problem. The files in the ~/.config/dconf folder contained settings for the background color (not in plain text). Clearing the directory solved the problem.

Going back to the main topic, I tested (besides 3.2.0) 3.3.7 and 3.4.0 mainline (precise) and 3.5.1 quantal (mainline). 3.3.7 and 3.4.0 virtual terminals (Ctrl-Alt-F?) work. With 3.2.0 and 3.5.1 the virtual terminal screen is corrupted.

rl

---

### Post by lulm on 2012-08-14
> **merlinux4 said:**
> Hi everybody,

this is my first message on the forum!

 VLC doesn't work too.



Hi! Same here, first message in the forum. Finally my Asus eee HA is working on 12.04, almost everything is working allright, but I'm still not able to reproduce video in full screen with any program. VLC simply doesn't work, I've tried MPLayer and SMPlayer, but nothing seems to work. 
If there is other threat about this problem, I apologize for using this one. 
Thank you!!

---

### Post by merlinux4 on 2012-08-16
> **lulm said:**
> Hi! Same here, first message in the forum. Finally my Asus eee HA is working on 12.04, almost everything is working allright, but I'm still not able to reproduce video in full screen with any program. VLC simply doesn't work, I've tried MPLayer and SMPlayer, but nothing seems to work. 
If there is other threat about this problem, I apologize for using this one. 
Thank you!!
Hi lulm, did you find any solution?

---

### Post by Horan on 2012-08-20
bump.

Same problems here, actually I haven't managed to get the grub's menu visible.

---

### Post by brunox1 on 2012-08-30
id just like to report that after installing ubuntu 12.10 i can finally use external vga monitor with on sony vaio p series netbook (vpcp113kx). 

only problem left for me is screen flickering but i dont know whats  causing it.

big thx to everyone for this driver!

---

### Post by mpw on 2012-08-30
> **brunox1 said:**
> 
only problem left for me is screen flickering but i dont know whats  causing it.


Same here. Any ideas about this?

---

### Post by SteffenBNielsen on 2012-08-30
I'm running 12.04 on my ASUS 1101HA and everything seems to work. My only problem is that the cursor of my mouse flickers when it's being moved over graphics elements or when the left mouse button is held down. Any ideas?

---

### Post by gaby81 on 2012-08-31
Does someone know, how to blacklist the default gma500 driver in Ubuntu 12.04.1?

---

### Post by TakeLifeEasy on 2012-09-16
For those that are testing 12.10, how is Gnome3 performing?  I did have Gnome 3 working under 12.04 but it was very slow...then all of a sudden, it no longer worked and booted into Gnome 2 shell.  Just wondering if Gnome 3 is now working again under 12.10.

---

### Post by bodhi.zazen on 2012-09-16
> **TakeLifeEasy said:**
> For those that are testing 12.10, how is Gnome3 performing?  I did have Gnome 3 working under 12.04 but it was very slow...then all of a sudden, it no longer worked and booted into Gnome 2 shell.  Just wondering if Gnome 3 is now working again under 12.10.

Gnome 3 + llvmpipe is slow. IMO llvmpipe is better integrated in Fedora (llvmpipe has been slow to be ported to Debian/Ubuntu, so typically Ubuntu lags by at least a version or two), but it is still slow last I tried it.

IMO, KDE has a decent trade off between eye candy and performance with the gma500, ymmv.

Otherwise try Xubuntu or lubuntu, either will give decent performance, but at a bit less eye candy.

---

### Post by modafokaxx on 2012-09-18
Hi everyone.
I,m running 12.10 with the 3.5.0-14 kernel and gma500_gfx driver (confirmed by ```
lsmod | grep gma
```) but the whole Unity experience is *very* slow.

From the system settings > details page I can see LLVMpipe is being used, which I imagine explain the slowness.

Am I the only one for whom 12.10 + gma500_gfx is painfully slow?

I've removed any specific Grub options I'd set in 12.04, so the kernel isn't booting with any options apart from "quiet splash". I've also just read through the whole thread but found no relevant info.

Any othe clues?

Many thanks!

---

### Post by auton on 2012-09-18
> **brunox1 said:**
> 
only problem left for me is screen flickering but i dont know whats  causing it.


Same issue here. **[FONT=Courier New]dmesg[/FONT]** tells me:
```

[10063.112608] [drm] GMBUS timed out, falling back to bit banging on pin 0 [gma500 gmbus disabled]

```over and over again, corresponding to the screen switching off briefly and back on - the "flickering".

Laptop is ASUS EeePC 1201HAB, kernel is 3.5.3-1, not sure where to go from here. I've tried Mint which seems to work without the flickering. However on both distro's the mouse does vanish at times as others have said. The flickering is the bigger issue, though.

---

### Post by bodhi.zazen on 2012-09-18
> **modafokaxx said:**
> Hi everyone.
I,m running 12.10 with the 3.5.0-14 kernel and gma500_gfx driver (confirmed by ```
lsmod | grep gma
```) but the whole Unity experience is *very* slow.

From the system settings > details page I can see LLVMpipe is being used, which I imagine explain the slowness.

Am I the only one for whom 12.10 + gma500_gfx is painfully slow?

I've removed any specific Grub options I'd set in 12.04, so the kernel isn't booting with any options apart from "quiet splash". I've also just read through the whole thread but found no relevant info.

Any othe clues?

Many thanks!

Read my post just above yours. llvmpipe is going to be slow.

IMO the version of llvmpipe has lagged in the ubuntu repositories (I've not looked recently). IMO you are better off either using k/x/lubuntu.

If you want "bleeding edge" llvmpipe, either compile the latest version yourself, look for a ppa, or try Fedora 18 (gnome spin).

---

### Post by ranomine on 2012-09-19
Dear All,

Has anyone got success in getting backlight keys to work on Vaio X (or P) using 
quantal (kernel 3.5.0-14) ?
I tried all settings (acpi_backlight=video or vendor) in grub.cfg with limited success so far.

Second question:
has anyone got a better modeline than the currently detected one at 29.9Hz) ?

Many thanks

Roch.

---

### Post by rafeuf on 2012-09-20
> **brunox1 said:**
> 
only problem left for me is screen flickering but i dont know whats  causing it.

I have same problem with 12.04. The flickering disappear after setting brightness lower then ~75%.

---

### Post by TakeLifeEasy on 2012-09-23
> **bodhi.zazen said:**
> Gnome 3 + llvmpipe is slow. IMO llvmpipe is better integrated in Fedora (llvmpipe has been slow to be ported to Debian/Ubuntu, so typically Ubuntu lags by at least a version or two), but it is still slow last I tried it.

IMO, KDE has a decent trade off between eye candy and performance with the gma500, ymmv.

Otherwise try Xubuntu or lubuntu, either will give decent performance, but at a bit less eye candy.


Yep, just installed Gnome Ubuntu 12.10 and it is still very slow. I just wish llvmpipe could be updated :(

---

### Post by bodhi.zazen on 2012-09-23
> **TakeLifeEasy said:**
> Yep, just installed Gnome Ubuntu 12.10 and it is still very slow. I just wish llvmpipe could be updated :(

llvmpipe is slow on Fedora 18. Performance is better, but still slow.

Personally I use kde or xfce rather then gnome.

---

### Post by gsedej on 2012-09-26
Hello.

I would like to use Asus EeePC 1101HA for presentations. But I can't get it working in 12.04 (nor with 12.10 kernel)

I have questions:
- Does VGA output work for anyone?
- If does, is it possible to change resolution on LVDS (native 1366 x 768, which does not work good with projectors)
- is there any effort to use EMGD 1.14 on Ubuntu 12.04 (even with downgrading xorg)?

Currently I am using 10.10 with EMGD and works ok, but I have no updates at all.

---

### Post by bodhi.zazen on 2012-09-26
> **gsedej said:**
> Hello.

I would like to use Asus EeePC 1101HA for presentations. But I can't get it working in 12.04 (nor with 12.10 kernel)

I have questions:
- Does VGA output work for anyone?
- If does, is it possible to change resolution on LVDS (native 1366 x 768, which does not work good with projectors)
- is there any effort to use EMGD 1.14 on Ubuntu 12.04 (even with downgrading xorg)?

Try booting with the projector plugged in.

> Currently I am using 10.10 with EMGD and works ok, but I have no updates at all.

There have been claims of getting the EMGD driver working, but I have not been able to get it working and no one has ever posted a working tutorial.

---

### Post by gsedej on 2012-09-27
Ubuntu 10.04 server will have support till 2015 and I will try to use it as desktop (apt-get install ubuntu-desktop).
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
(maybe there is even chance for getting OpenGL ES2.0 and WebGL running)

There is O2 Joggler Ubuntu which claim to have to have EMGD 1.14 (xorg 1.9) running on 12.04 but I was unable to boot from USB on my eee.(just flashing "_" when should be grub)
[http://joggler.exotica.org.uk/ubuntu/](http://joggler.exotica.org.uk/ubuntu/)
Blog: [http://www.jogglerwiki.com/forum/viewtopic.php?f=2&t=536](http://www.jogglerwiki.com/forum/viewtopic.php?f=2&t=536)

There is also EMGD Precise PPA, but it was updated 2011-12 (12.04 alpha?) from Thomas-Karl Pietrowski. I didn't tried it yet.
[https://launchpad.net/~thopiekar/+archive/emgd/+index?field.series_filter=precise](https://launchpad.net/~thopiekar/+archive/emgd/+index?field.series_filter=precise)

That's everything I was able to find.
Everything else that's trying to use EMGD is dead pretty much (for year or two).

I did succeed getting "good" desktop on 12.04 with KDE :) (without composition, it's VERY slow on Z520).

---

### Post by dimos15 on 2012-09-28
Someone said on a forum he has ubutnu 12.04 with emgd 1.14 using this
[https://launchpad.net/~jools/+archive/emgd-xorg1.9]("https://launchpad.net/%7Ejools/+archive/emgd-xorg1.9")

---

### Post by bodhi.zazen on 2012-09-28
> **dimos15 said:**
> Someone said on a forum he has ubutnu 12.04 with emgd 1.14 using this
[https://launchpad.net/~jools/+archive/emgd-xorg1.9]("https://launchpad.net/%7Ejools/+archive/emgd-xorg1.9")

You should ask this person to update the wiki or post specific instructions as no one has been able to replicate that.

Without details, nothing more then unsubstantiated claims, wishful thinking (see the post right above yours).

---

### Post by exobuzz on 2012-09-28
> **bodhi.zazen said:**
> You should ask this person to update the wiki or post specific instructions as no one has been able to replicate that.

Without details, nothing more then unsubstantiated claims, wishful thinking (see the post right above yours).

you say no-one but there are plenty of joggler users running the 12.04 xubuntu image. It is specifically made for the joggler hardware, but I know at least one other person who has the emgd drivers running on another device using my ppa. I have already explained how to do it on this forum, regarding apt preferences file and sources.list to pin xserver to 1.9. in [http://joggler.exotica.org.uk/source/overlay-2012-06-14.tar.gz](http://joggler.exotica.org.uk/source/overlay-2012-06-14.tar.gz) you can find the sources.list and apt pinning configs.

---

### Post by bodhi.zazen on 2012-09-28
> **exobuzz said:**
> you say no-one but there are plenty of joggler users running the 12.04 xubuntu image. It is specifically made for the joggler hardware, but I know at least one other person who has the emgd drivers running on another device using my ppa. I have already explained how to do it on this forum, regarding apt preferences file and sources.list to pin xserver to 1.9. in [http://joggler.exotica.org.uk/source/overlay-2012-06-14.tar.gz](http://joggler.exotica.org.uk/source/overlay-2012-06-14.tar.gz) you can find the sources.list and apt pinning configs.

Not sure what joggler is, but if you have it working in Ubuntu you should update the wiki page / provide documentation so others may follow.

---

### Post by gsedej on 2012-09-29
> **bodhi.zazen said:**
> Try booting with the projector plugged in.


I tried it and i get cloned image in both displays 1024x768. It's somehow ok. But I don't see 2 displays in xrandr or any other resolution. Also on laptop screen has "wierd" image around 1024x768 region (remider from booting).

I also tried 10.04.4
[LIST]
I was able to use GMA500 team PSB PPA, and 3D works "good" (regarding actually slow hardwer) I get 20FPS in Neverball. Metacity woks fine with composition (I had to remove compiz due to confict). **EDIT**: OpenGL is bad with everythig else: even OpenArena is unplayable. (but ok for World of Goo)
[*] I also tried GMA500 team EMGD PPA but i couldn't see it working, even tough i modprobe emgd, glxinfo always showed software rast. **EDIT**: It's mismatch with Xorg server: Bug: [https://answers.launchpad.net/emgd/+question/182662](https://answers.launchpad.net/emgd/+question/182662). So no EMGD for 10.04
[/LIST]
So 10.04 will be supported till 2013.4. 
Let's hope mr. Alan Cox gives some

BTW: EMGD from gma500 team ([https://launchpad.net/~gma500/+archive/emgd](https://launchpad.net/~gma500/+archive/emgd)) suggest to use some scripts that were on dropbox, but now missing.
```
dl.dropbox.com/u/1338581/gma500/emgd-lucid.sh
dl.dropbox.com/u/1338581/gma500/emgd-maverick.sh
```
**does someone have copy of them somewhere?**

---

### Post by exobuzz on 2012-09-29
> **bodhi.zazen said:**
> Not sure what joggler is, but if you have it working in Ubuntu you should update the wiki page / provide documentation so others may follow.

The joggler is a internet appliance - looks like a photoframe - [http://en.wikipedia.org/wiki/O2_Joggler](http://en.wikipedia.org/wiki/O2_Joggler) - due to the other changes needed to get everything working on this, I couldn't be sure to write proper step by step instructions. But someone with some more usual device with poulsbo who has some experience could do the xserver downgrade as explained and write it up. It's not ideal of course as you are then running a much older xserver, and other changes may be needed depending which display manager. if using lightdm for example you need to modify it so it doesn't pass an unsupported parameter to the xserver (-background i think). I have modified lightdm packages here [https://launchpad.net/~jools/+archive/joggler](https://launchpad.net/~jools/+archive/joggler)

I would agree this is not a pleasant/easy process and certainly if someone doesn't specifically need emgd, using the open source driver is preferable. In our case, we want to use hardware video decoding with xbmc, so it is needed.

---

### Post by gsedej on 2012-09-29
> **exobuzz said:**
> The joggler is a internet appliance - looks like a photoframe - [http://en.wikipedia.org/wiki/O2_Joggler](http://en.wikipedia.org/wiki/O2_Joggler) - due to the other changes needed to get everything working on this, I couldn't be sure to write proper step by step instructions. But someone with some more usual device with poulsbo who has some experience could do the xserver downgrade as explained and write it up. It's not ideal of course as you are then running a much older xserver, and other changes may be needed depending which display manager. if using lightdm for example you need to modify it so it doesn't pass an unsupported parameter to the xserver (-background i think). I have modified lightdm packages here [https://launchpad.net/~jools/+archive/joggler](https://launchpad.net/~jools/+archive/joggler)

I would agree this is not a pleasant/easy process and certainly if someone doesn't specifically need emgd, using the open source driver is preferable. In our case, we want to use hardware video decoding with xbmc, so it is needed.

Do you have any idea why your .iso ([http://joggler.exotica.org.uk/img/xubuntu_12.04-v1.1-ext4.img.gz]("http://joggler.exotica.org.uk/img/xubuntu_12.04-v1.1-ext4.img.gz")) doesn't boot on my Asus Eee 1101HA ([http://uk.asus.com/Eee/Eee_PC/Eee_PC_1101HA_Seashell/#specifications]("http://uk.asus.com/Eee/Eee_PC/Eee_PC_1101HA_Seashell/#specifications")). It has same CPU (Atom Z520).

Maybe I could help porting your PPA to "standard" hardware? (I do not have much xorg compiling experience)

---

### Post by exobuzz on 2012-09-29
> **gsedej said:**
> It has same CPU (Atom Z520).

Maybe I could help porting your PPA to "standard" hardware? (I do not have much xorg compiling experience)

it is designed for the o2 joggler hardware. from the efi boot partition etc. it won't work on a machine without efi, and even then the kernel is tailored to the joggler hardware. It is designed work on joggler and openframe 2.0 devices.

you don't need to port the "ppa". the packages there will be fine on your machine. but I probably can't help with complete xorg config for your machine. if you know how to configure emgd in xorg.conf for your hardware, and are confident with apt it's possible.

---

### Post by mpw on 2012-09-30
Hello,

when I play a video with mplayer and switch to fullscreen, the video is displayed in the same size and boardered with black.

Can the gma500 scale Videos anyway? Well more exactly: Can the driver scale the videos? I'm using mplayer-vaapi.

Bye
MPW

---

### Post by gsedej on 2012-10-01
> **mpw said:**
> Hello,

when I play a video with mplayer and switch to fullscreen, the video is displayed in the same size and boardered with black.

Can the gma500 scale Videos anyway? Well more exactly: Can the driver scale the videos? I'm using mplayer-vaapi.

Bye
MPW

What version of Ubuntu and which driver (and version) do you use?
The current supported is gma500_gfx an open source driver, which works for desktop, but no accelerated 3D or composition (Compiz). It also does not have accelerated video en/decoder.

The EMGD or PSB drivers are unsupported in current Ubuntus

---

### Post by blugeco on 2012-10-01
> **mpw said:**
> 
Can the gma500 scale Videos anyway? Well more exactly: Can the driver scale the videos? I'm using mplayer-vaapi.


Hi,

I am using **mplayer** and was having the same problem. I fixed it as explained [here]("http://ubuntuforums.org/archive/index.php/t-77329.html").

Basically, I added > zoom="1" to the ~/.mplayer/config file.

It works quiet well for me.

Cheers,

blugeco

---

### Post by Anaesthisia on 2012-10-01
I read that Unity 2d has been scrapped in 12.10, leaving the CPU with the task of helping with rendering things the GPU cannot handle? If this is correct, I guess upgrading will not be very suitable for those of us who only have 1GB of RAM?

***A***

---

### Post by bodhi.zazen on 2012-10-02
> **Anaesthisia said:**
> I read that Unity 2d has been scrapped in 12.10, leaving the CPU with the task of helping with rendering things the GPU cannot handle? If this is correct, I guess upgrading will not be very suitable for those of us who only have 1GB of RAM?

***A***

I am guessing you are referring to llvmpipe ?

And yes, llvmpipe is slow.

I highly advise you switch to K/X/Lubuntu

---

### Post by Anaesthisia on 2012-10-02
> **bodhi.zazen said:**
> I am guessing you are referring to llvmpipe ?

And yes, llvmpipe is slow.

I highly advise you switch to K/X/Lubuntu

I'm not sure exactly what technologies are involved, I only read that Ubuntu would take away the Unity 2D option in 12.10.

I guess I could still upgrade to 12.10, then, but install Xfce or KDE desktop? I do like the Unity greeter, so I might want to keep that.

**A**

---

### Post by sandyd on 2012-10-05
**Removed posts on EMGD**
Please read the first post.

> Note: This thread is [COLOR="Red"]NOT[/COLOR] for discussing the depreciated EMGD driver. If you need support for the EMGD please contact Intel.

A separate EMGD thread can be created as soon as the gma500 team provides stable packages and adequate documentation.

As said, EMGD is depreciated, and breaks systems.

---

### Post by grahamst on 2012-10-17
I've been away from this thread for a while and have just been catching up.

Have I got this right?

gma500_gfx at last works out of the box with 12.10. However, it won't be usable because Unity 2D has been scrapped and llvmpipe, which has to take over the Unity 2D work, is really slow. There are solutions (try a different version of Ubuntu, install a different graphical environment like KDE) but they all involve fiddling with the standard distribution, which means my Acer AO751h won't work out of the box - disappointing.

I'm willing to do a bit of fiddling, but I'm no expert. Given that 12.04 has got long-term support for another 18 months and I only want to run basic applications (mostly web, mail, office stuff), will I be better off not upgrading beyond 12.04?

Graham

---

### Post by mikewhatever on 2012-10-17
> **grahamst said:**
> I've been away from this thread for a while and have just been catching up.

Have I got this right?

gma500_gfx at last works out of the box with 12.10. However, it won't be usable because Unity 2D has been scrapped and llvmpipe, which has to take over the Unity 2D work, is really slow. There are solutions (try a different version of Ubuntu, install a different graphical environment like KDE) but they all involve fiddling with the standard distribution, which means my Acer AO751h won't work out of the box - disappointing.

I'm willing to do a bit of fiddling, but I'm no expert. Given that 12.04 has got long-term support for another 18 months and I only want to run basic applications (mostly web, mail, office stuff), will I be better off not upgrading beyond 12.04?

Graham

That's about right, though I am not sure what you mean by "fiddling with the standard distribution". If you want Kubuntu, Xubuntu or Lubuntu installed, the 12.10 release should, hopefully, work without fiddling. Also, 12.04 is supported for 5 years as an LTS, whereas 12.10 is a regular release supported for 18 months.

---

### Post by grahamst on 2012-10-18
Thanks. Apologies for mixing up the support periods for LTS and regular distributions with their update frequency.

By the 'standard distribution' all I meant was the version downloadable from [http://www.ubuntu.com/](http://www.ubuntu.com/) - as far as I can see, the others all call themselves 'derivatives'.

I've been using 'standard' Ubuntu ever since a special netbook version was released. That no longer applies, and it may be that one of the other versions is now more suitable for my GMA500 netbook. However, given that (unlike most people who post to this thread) I don't want to spend a lot of time tinkering with my OS/GUI, I think I'll probably stick with 12.04, as it works for what I want to do and the support period will almost certainly last longer than my netbook (which is already 2.5 years old).

Thanks to everyone who has contributed both to this thread and to the old 'Performace' thread - you've helped to make my netbook workable.

Graham

---

### Post by gsedej on 2012-10-23
Hello!

I would just like to confirm that **Kubuntu 12.10 on GMA500 works very good** for desktop use! *(Atom z520 in my case)*

I was able to run KDE plasma desktop smoothly on **2 monitors LVDS 1366x768 + VGA 1600x1050** with compositin (xrender).

(There is still issue with not being able to change resolution for LVDS, I posted bug here [https://bugs.freedesktop.org/show_bug.cgi?id=55564]("https://bugs.freedesktop.org/show_bug.cgi?id=55564"))

*Also, there is no OpenGL or video acceleration*

---

### Post by grahamst on 2012-10-24
OK - it's good that Kubuntu works well. I can confirm that standard (GNOME) Ubuntu 12.10 is awfully slow. Even allowing for the fact that I'm running it from a USB drive, it's really sluggish - you can see windows being crreated and taken down in stages, the scrolling Unity icons on the left of the screen jerk up and down very slowly and it takes a while for the menu bar at the top to change, even after the initial loading. Scrolling up and down web pages is also sluggish and jerky.

No surprise after what's been written in this forum, but even if the installed version is a bit faster I couldn't live with it. It's a shame, because the GMA500 driver really does work without any modification being needed.

I'll try downloading Kubuntu and will see how much difference there is. I'll also try GNOME Ubuntu on my older, non-GMA500 netbook to see how that compares.

Graham

Graham

---

### Post by GreatEmerald on 2012-10-24
So far I still can't get the screen to turn off on my Oak Trail device. I can now make it decrease the brightness, but not turn it off... Neither using xset nor otherwise. It just makes the screen "shine black".

Has anyone else experienced something like that? Also, how is it related to the graphics driver, anyway? Directly, or could it actually be a bug in the screen drivers or ACPI or something else?

---

### Post by TakeLifeEasy on 2012-10-25
My understanding is that Gnome 3 on Fedora works well with the GMA500 chipset.  Does anyone know how they managed this and if these tweaks can be ported to Ubuntu 12.10

---

### Post by mikewhatever on 2012-10-26
> **TakeLifeEasy said:**
> My understanding is that Gnome 3 on Fedora works well with the GMA500 chipset.  Does anyone know how they managed this and if these tweaks can be ported to Ubuntu 12.10

That's not my experience. Fedora 18 with Gnome3 is rather slow as well.

---

### Post by TakeLifeEasy on 2012-10-26
That is interesting as I have always thought Fedora had improved the performance.  This is worrying, it looks like this chipset may never work well with Gnome 3:(  Is anyone away of any work going on trying to improve and/or testing this?  Just wondering if there is a PPA I can subscribe to to help further testing?

---

### Post by mikewhatever on 2012-10-26
> **TakeLifeEasy said:**
> That is interesting as I have always thought Fedora had improved the performance.  This is worrying, it looks like this chipset may never work well with Gnome 3:(  Is anyone away of any work going on trying to improve and/or testing this?  Just wondering if there is a PPA I can subscribe to to help further testing?

Indeed, the llvmpipe performance has improved, most notably on multicore 64bit CPUs, none of which applies to Intel's Z5xx Atom series. Z5xx Atoms are just not powerful enough for GPU emulation.

Gnome3 and Compiz/Unity are not suitable for the gma500 based machines, kind of like not every key fits every lock.  Modern Linux desktops are being geared to OpenGL 3+ capable hardware. Luckily, there are other options that work decently well.

There aren't any PPAs worth subscribing to, but you might want to wach out once in a while for news on gma500 and Linux. Keep the expectations real though, as there aren't many incentives for anyone to work on a proper driver.

---

### Post by mpw on 2012-10-27
Hello,

I already got much help from here. Thanks for that. Once again I have a question:

I'm using Ubuntu 12.04 on a Sony Vaio Series X with a gma500 ofc. Now I'd like to use an external monitor. When I connect it and reboot, the image is set to 1024x768 on both montiors and the image is mirrored. Is there any change to switch the internal and external monitors to different resolutions and expand the desktop on both screen?

Which is the maximum resolution the gma500 is cappable of? My internal montior uses 1367x768.

Bye
MPW

---

### Post by Paul Debrione on 2012-10-28
Hi there,

regarding 12.10 and the GMA500 chipset, I take it that it's basically a 'don't bother situation'?

I just downloaded 12.10 and installed it on an Acer One A0751h. It installed perfectly and it does look sweet as long as I don't actually do anything with the computer. It is staggeringly slow, I mean 286 slow. It's running a tiny anemic 1.3ghz Atom with 2 GB of memory and the cpu is running flat out. when I look for a video card in the 'Details' app it's reported as 'Unknown'. The OS reports that there is no graphics card and so all the screen handling is being done by the cpu. System Monitor show the cpu at 100% utilization  It has the correct resolution and it appears to be doing 3D since the widows once they turn up have a bit of drop shadow around them. Is this machine actually using the poulsbo driver or did it not for some reason load it? This is a straight generic kernel downloaded yesterday. If it didn't load the Poulsbo driver how do I get it into the machine since the Proprietary Driver App appears to be missing off the System Settings Window.

Is it worth me actually doing anything with this or shall I 'BlendTech' this netbook (or worse, take it back to Vista)?

---

### Post by mikewhatever on 2012-10-29
> **Paul Debrione said:**
> Hi there,

regarding 12.10 and the GMA500 chipset, I take it that it's basically a 'don't bother situation'?

I just downloaded 12.10 and installed it on an Acer One A0751h. It installed perfectly and it does look sweet as long as I don't actually do anything with the computer. It is staggeringly slow, I mean 286 slow. It's running a tiny anemic 1.3ghz Atom with 2 GB of memory and the cpu is running flat out. when I look for a video card in the 'Details' app it's reported as 'Unknown'. The OS reports that there is no graphics card and so all the screen handling is being done by the cpu. System Monitor show the cpu at 100% utilization  It has the correct resolution and it appears to be doing 3D since the widows once they turn up have a bit of drop shadow around them. Is this machine actually using the poulsbo driver or did it not for some reason load it? This is a straight generic kernel downloaded yesterday. If it didn't load the Poulsbo driver how do I get it into the machine since the Proprietary Driver App appears to be missing off the System Settings Window.

Is it worth me actually doing anything with this or shall I 'BlendTech' this netbook (or worse, take it back to Vista)?

You can check with **lspci -nnk | grep -A3 VGA** .
It probably does use the correct driver, which simply isn't capable of handling Unity. You can run Ubuntu 12.04 with Unity2d on that, or else Kubuntu(without effects), Xubuntu and Lubuntu.

---

### Post by Karosieben on 2012-11-02
Hello @ all,

i'm trying to install kubuntu 12.10 desktop i386 on my Dell Latitude ST (Intel Atom Z670)

The installation works fine, but after booting from the internal SSD there is no X-Server, only shell-Login.

My kernel is 3.5.0-17-generic i686

My modified options in /etc/default/grub are:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash sdhci.debug_quirks=4" Note: the sdhci option is needed for the Atheros WLAN/BT-Card. (Dell 1535C)

I tried all suggestions from []("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo")[the Wiki about the GMA 500]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") for ubuntu 12.04, nothing gets the gui working and the last one (915resolution) is getting my system stuck before loading grub.

Any ideas?

Regards,
Karosieben

---

### Post by trewelu on 2012-11-03
> **mpw said:**
> Hello,

I already got much help from here. Thanks for that. Once again I have a question:

I'm using Ubuntu 12.04 on a Sony Vaio Series X with a gma500 ofc. Now I'd like to use an external monitor. When I connect it and reboot, the image is set to 1024x768 on both montiors and the image is mirrored. Is there any change to switch the internal and external monitors to different resolutions and expand the desktop on both screen?

Which is the maximum resolution the gma500 is cappable of? My internal montior uses 1367x768.

Bye
MPW

Hi, I'm using vaio P in archlinux, so it might not 100% the same but this is what I did. I need to use modesetting driver instead of fbdev one (I don't know what is the default for ubuntu).

Then I query xrandr for supported external resolution and display name. (I don't attach it to any external monitor when I did this
```
[min@sakura xfce4-volumed]$ xrandr 
Screen 0: minimum 320 x 200, current 1600 x 768, maximum 2048 x 2048
LVDS-0 connected 1600x768+0+0 0mm x 0mm
   1600x768       30.0*+   59.9  
   1368x676       59.7  
   1280x614       59.7  
   1256x600       59.8  
S-video-0 disconnected
S-video-1 disconnected
VGA-0 disconnected

```

finally set the resolution

```
"xrandr --output LVDS-0 --mode 1600x768 --rate 59.9 --output VGA-0 --mode 1920x1080 --below LVDS-0"

```

As you can see the maximum resolution is 2048x2048, so you need to stack it top and bottom instead of left and right

---

### Post by mpw on 2012-11-03
Hello,

thanks for your answer, but xrandr just tells me:

```
mpw@MPWs-Netbook:~$ sudo xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1366 x 768, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768        0.0* 
```

---

### Post by trewelu on 2012-11-04
Do you have a Xorg configuration? You might want to check archlinux wiki for pulsbo/gma500. It has a section for dual monitor. I don't how much adjustment you will ned to make the step work on ubuntu.

Probably someone who is currently using ubuntu will be able to help you better.

---

### Post by cataclop on 2012-11-06
Hello,

Thanks to the forum Archlinux, I could have several things running, and had a real performance boost :
&#8722; I installed xserver-xorg-video-modesetting from [this ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") ;
&#8722; I put that in /usr/share/X11/xorg.conf.d/00-modesetting.conf (create it if it doesn't exist) :
```
Section "Device"
    Identifier  "gma500_gfx"
    Driver      "modesetting"
    Option     "SWCursor"       "ON"
EndSection
```
&#8722; then I restarted X (disconnect/reconnect).

Doing that gave me the ability to :
&#8722; have 2 different screens thanks to xrandr (I installed grandr to have a gui) ;
&#8722; use icc color profiles thanks to argyllcms.

Please forgive me if I made English mistakes (I'm French) ; hope that will help.

---

### Post by SuperMaximus on 2012-11-11
Dear Experts,
 
I am using Lubuntu 11.10 on my Sony VAIO P (P31ZRK) with EMGD drivers for GMA500 and overall performance is tolerable, however I can't get video accelerated playback. With GNOME mplayer none of video acceleration menthods work (video 720p is sluggish), in case of
mplayer -va vaapi -vo vaapi [file] 
mplayer says Unknown option on the command line: -va
 
I assume I need to install Mplayer with video acceleration.
Please help me, I am not experienced linux user...

---

### Post by coffeecat on 2012-11-11
> **SuperMaximus said:**
> I am using Lubuntu 11.10 on my Sony VAIO P (P31ZRK) with EMGD drivers for GMA500 and overall performance is tolerable, however I can't get video accelerated playback.

Please read through this thread. Some comments on EMGD which you appear to have missed:

> **bodhi.zazen said:**
> 
[B][COLOR="DarkRed"]Note: This thread is NOT for discussing the depreciated EMGD driver. If you need support for the EMGD please contact Intel.

A separate EMGD thread can be created as soon as the [gma500 team](https://launchpad.net/gma500) provides stable packages and adequate documentation.[/COLOR][/B]

> **mikewhatever said:**
> Let's get some facts straight first:

1. Ubuntu devs have never provided support for EMGD. It's a closed source driver released by Intel, and never has it been the default one. That also means that there has been no switch from EMGD to gma500_gfx.

2. EMGD is not made for Ubuntu, and because of the way it is tied to the kernel and xserver versions, it doesn't work (in Ubuntu) without some major adjustments (xserver downgrade, etc). gma500_gfx, on the other hand is built in, and, though limited, works almost out of the box in Ubuntu and any other distro.

3. Some of the community members (aka gma500 team) were able to make EMGD work in older Ubuntu releases. That work is still available, and is free to use as you see fit. However, the efforts have proved unsustainable in the long run, and I do not know if they will be resumed. As far as I know, EMGD doesn't work at all in 12.04, so you are welcome to take up the job.


> **bodhi.zazen said:**
> 
There have been claims of getting the EMGD driver working, but I have not been able to get it working and no one has ever posted a working tutorial.

> **gsedej said:**
> 
The EMGD or PSB drivers are unsupported in current Ubuntus

> **sandyd said:**
> 
As said, EMGD is depreciated, and breaks systems.

---

### Post by SuperMaximus on 2012-11-12
coffeecat,

Considering this situation I consider reverting to Pulsbo drivers (I hope they'll work well with Lubuntu 11.10, which I'm using).
Can you advise me where could I download compiled mplayer-vaapi for usage with VA & Poulsbo?

---

### Post by TakeLifeEasy on 2012-11-17
Thanks for all the responses on Gnome 3.  I am still using 12.10 but use it with the Gnome faillback and it seems "usable".  From reading the posts above, it does seem this is the end of the life for by Dell mini 1010.  It has never worked properly and I have gone from an Intel lover to and Intel hater as they have done nothing to open the code for the driver. Maybe I can use this as a mini file server of something.

I will keep a eye out for any update on the driver in the hope someone can find a miracle!

All I can say is thank you to all the developers who have put so much effort and time into this.  Without those guys, I would have binned this rubbish laptop years ago.

---

### Post by mpw on 2012-12-08
Hello,

I tried to use the modesetting-driver to be able to use xrandr. I installed the package from the repo and added the config file.

But when I reboot, the screen stays black. I use Ubuntu 12.04 on a Sony Vaio X series.

Grüße
MPW

---

### Post by ferry_toth on 2013-01-29
Actually instructions have been published here (albeit for Linux Mint): [http://www.fit-pc.com/forum/viewtopic.php?f=68&t=2991](http://www.fit-pc.com/forum/viewtopic.php?f=68&t=2991)

Instead of dowloading the emgd drivers from their web site I use the ppa ppa:jools/emgd-xorg1.9 and get mplayer-vaapi from ppa:jools/joggler.

None of this is supported by ubuntu though. And downgrading your kernel is REALLY not something you should do if you are not prepared to loose all your data.

---

### Post by mpw on 2013-03-11
Hello,

as we all know, the main development for the gma500 was done by Alan Cox. He's gone now. Is there any team working on the psb_gfx driver right now? Or are there any plans to patch the EMGD 1.16 for Kernel 3.5 + X-server 1.12? Or did the development stop?

I'm really looking for a gma500 driver with vaapi on actual systems... ;-)

Linux Mint 13 with downgraded xserver is not a good option for me, as my touchpad needs at least xserver 1.10 to be supported.

Bye
MPW

---

### Post by mikewhatever on 2013-03-12
I don't think anyone has been developing psb_gfx, following its creation. Alan Cox may have maintained it, making sure it works with newer kernels, and fixing bugs, but there haven't been any news feature wise.
EMDG has been developed by Intel, but the company hasn't shown any interest in a release that would work on Ubuntu, and as GMA500 is already 5 years old, I very much doubt that would change.

---

### Post by soapstarjoe on 2013-03-30
Hey, anyone gotten backlight to work with vaio-p and 12.04? I get the on screen brightness control display when I press the keys, but no actual change in brightness. Googling my heart out I've only found two suggestions, neither of which have worked:

1) "acpi_osi=Linux acpi_backlight=vendor" grub options--display turns off after grub2 ) creating a xorg.conf file with backlight options (can't find the link at the moment:/ )

In 10.10 + psb_gfx ppa, I used to be able to use sudo setpci -s 00:02.0 F4.B=10 to set the brightness on the commandline, but no love since I installed 12.04

---

### Post by mikewhatever on 2013-03-30
What do you get from **ls /sys/class/backlight/**?

---

### Post by soapstarjoe on 2013-03-30
> **mikewhatever said:**
> What do you get from **ls /sys/class/backlight/**?

$ ls /sys/class/backlight/
acpi_video0  psb-bl

when I manually manipuate psb-bl, it actually changes values!

---

### Post by mikewhatever on 2013-03-31
Great! Try using [these scripts]("http://forums.bodhilinux.com/index.php?/topic/5985-brightness-scripts/"), obviously, modified for you particular needs. 
Hope it works.

---

### Post by Wenhao Li on 2013-04-01
I think the wiki helps a lot.

---

### Post by shurup on 2013-04-25
Hi guys!

I'm using GMA500 on a tablet with Ubuntu 12.10 Quantal. Everything is nice except for one little thing &#8212; resuming from suspend / hibernate. I'm using "pm-hibernate --quirk-vbemode-restore" for testing. After resuming everything seems to work but the video is totally "trashed". I mean, it's only garbage everywhere (in command line & Xorg). However, I can see blinking cursor in the command line and blindly login, run some commands to see a bit of green garbage &#9786;

I've tried all the things I've googled & thought about:
* fbdev / modesetting driver in /usr/share/X11/xorg.conf.d/20-gpu.conf;
* xserver-xorg-video-fbdev from Ringtail and from xorg-edgers (however, the problem should be on the kernel level because of being not only in the X, shouldn't it?);
* all the quirks as pm-hibernate arguments and in /etc/pm/config.d/gma500;
* edited, moved, removed scripts in /usr/lib/pm-utils/sleep.d (98video-quirk-db-handler, 99video, even tried to add 99remove-annoying-quirks);
* tried a lot of kernel options in /etc/default/grub (my current GRUB_CMDLINE_LINUX_DEFAULT is "quiet splash mem=1920mb console=tty1 acpi=force"; also tried nomodeset, noacpi, and others);
* updated kernel to 3.6.3-030603-generic from mainline.

"Fix suspend" from [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) looks like the common panacea. But not in my case. Any ideas? Thanks a lot in advance!


P.S.
# lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:4102] (rev 04)
        Subsystem: Intel Corporation Device [8086:4102]
        Kernel driver in use: gma500
        Kernel modules: gma500_gfx

---

### Post by laune on 2013-04-27
I installed linux mint 14 on my netbook with GMA500 accer. If I choose to use cinnamon performance drops dramatically. Questions: supported the GMA500 (Poulsbo) gma500_gfx for mint 14? or what is more recommendable?

(Eu instalei o linux mint 14 em meu netbook accer com gma500. Se opto por usar o cinnamon o desempenho cai drasticamente. Perguntas: há suporte no GMA500 (Poulsbo) gma500_gfx para o mint 14? ou o que é mais recomendável?)

---

### Post by ahallubuntu on 2013-05-02
> **mpw said:**
> Hello,

I tried to use the modesetting-driver to be able to use xrandr. I installed the package from the repo and added the config file.

But when I reboot, the screen stays black. I use Ubuntu 12.04 on a Sony Vaio X series.


I had the same problem on an Acer AO751H that has Ubuntu 12.04.1 on it.  The Wiki instructions (to use ppa:xorg-edgers/ppa ) result in a black screen upon reboot.  I had to go into recovery mode and remove the modesetting driver and the PPA, then I was able to boot again.

FYI, I also tried upgrading to 12.04.2 from 12.04.1 and that broke a couple of things.  So I am starting over and installing 12.04.2 from scratch.  Everything works fine except the trick to make suspend/resume work correctly needs a tweak:  the Ubuntu Wiki for Poulsbo/GMA500 says to do this:

```
gksu gedit /etc/pm/config.d/gma500
Add in the following code and save the file:

ADD_PARAMETERS='--quirk-vbemode-restore'

```

For 12.04.2, you need to remove one of leading dashes for the parameter, so the added line should be:

ADD_PARAMETERS='-quirk-vbemode-restore'

otherwise, you'll get a black screen at resume.  Remove the one dash and it works great.  I figured this out from the ArchLinux Wiki:

[https://wiki.archlinux.org/index.php/Poulsbo](https://wiki.archlinux.org/index.php/Poulsbo)

FYI, modesetting seems to work by default in 12.04.2 .  It's a shame I've had to spend hours re-installing 12.04.2 from scratch, though...

---

### Post by konas on 2013-05-26
Has anyone tried kernel 3.10 rc2? suspend works perfectly on my Acer Aspire 751h, it wakes up in a second, never worked like that before.

---

### Post by ahallubuntu on 2013-06-01
I've used Ubuntu 12.04.2 on my AO751h netbook for a couple of weeks full time.  It works pretty well except for two things: 1) a very weird freezing bug (see below) and 2) I still can't get hibernation to work reliably.  I guess I can live without hibernation, because suspend/resume seems very reliable.  With 11.04, resume would not work maybe 1/5 times and I'd have to do a hard shut down to clear it.  I suspended/resumed dozens of times in the last few weeks and never needed to do that, even once.

Now the weird freezing bug: when playing a video or even listening to an mp3 file, I noticed that once in a while, the media would sort of freeze until I hit a key or moved the mouse.  It wasn't a complete freeze; the audio would repeat in a 1/2 second loop, endlessly.  Very odd.  I wasn't even sure how to describe the bug let alone fix it, but it was extremely annoying.  Think about watching a movie on an airplane and having to move your mouse every minute (sometimes more often, sometimes less) just to get it the movie to continue playing.

After some research, I found that this bug is not entirely uncommon.  It appears to be related to be related to low power states of the CPU and can happen on different systems.  I guess somehow the CPU can get stuck in the lowest power state and nothing happens until something wakes it up.  In more advanced systems, you may be able to disable certain power management features in BIOS Setup - but of course, Acer's BIOS options for the AO751h are extremely minimal and no such options are available.

I found this article - rather, the first answer by Michael Goldshteyn - extremely helpful:

[http://stackoverflow.com/questions/12111954/context-switches-much-slower-in-new-linux-kernels](http://stackoverflow.com/questions/12111954/context-switches-much-slower-in-new-linux-kernels)

It seems that between kernel 3.2 and 3.5, for Intel CPUs, the cpu_idle driver changed from the old one called "acpi_idle" to a newer (better?) driver called "intel_idle."  In any event, I never saw this problem on the AO751h with the older kernels, so I decided to revert the older "acpi_idle" - and after doing so - no freezes!  The problem was easiest to reproduce simply by playing a video in totem, closing all other windows, running on battery, and disabling the wireless card - and after a half hour of playing I haven't had the video freeze once!

Anyway, using the link above, here's how I got the kernel to revert to "acpi_idle" in Ubuntu 12.04.2:

Edit the file /etc/default/grub:

```
gksu gedit /etc/default/grub
```

and find the familiar line "GRUB_CMDLINE_LINUX_DEFAULT" where you've probably already added other options to make the AO751h work properly.  To the list of options already there, add this one (separated by a space from the other options on that line):

```
intel_idle.max_cstate=0
```

Save the file, then run:

```
sudo update-grub
```

Then reboot.

This doesn't actually disable power saving states; according to Michael Goldshteyn, it simply tells the kernel to revert to the old acpi_idle driver.  I verified that indeed this is exactly what happens on my AO751h.  I don't know what the effect of this change might be on, say, battery life - for all I know, battery life may be even better with the old driver on the AO751h.  Who knows?  The Atom CPU doesn't consume much power, anyway.  I'm willing to live with the same kind of battery life/performance we got with the older kernels, which is all this change really does.

---

### Post by ahallubuntu on 2013-06-01
I realize after posting the above that the freezing issue I mention may not be directly related to the gma500_gfx driver - but it will affect many people who use this driver (e.g. netbooks), probably not just users of the AO751h.  I still hope it helps someone!

---

### Post by mpw on 2013-11-17
@ahallubuntu: Thanks for that hint. 

Kernel 3.12 is able to use two dashes again. By the way, I can confirm my Sony Vaio X series runs nicely with Kernel 3.12.

One problem left: After standby, the screen brightness is resettet to maximum. Not that a big problem, but if someone has a nice fix, I'd take it.

/edit: I just found out, that Kernel 3.12 does not need the special standby settings "-quirk-vbemode-restore" anymore! I removed the file /etc/pm/config.d/gma500, which contained the quirk-vbemode-restore-parameter and just did "sudo pm-suspend" and it worked! And the awaking is much much faster now! That's cool.

Thanks to the (unkown to me) kernel developer who fixed that!

But still remaining the brightness maximum issue.

---

### Post by mikewhatever on 2013-11-23
@mpw You can use a similar script to reset the screen brightness on wakeup. It would look something like this:
```

#!/bin/bash

case "$1" in
        thaw | resume)
        echo X > /sys/class/backlight/acpi_video0/brightness
        ;;
esac

```
...now, to figure out the X value (unless you already know), change screen brightness with the keybard, and look at outputs of 
```

cat /sys/class/backlight/acpi_video0/brightness

```
Finally, create a file named 99-brightness in /etc/pm/sleep.d/, make it executable, and you are good to go.

---

### Post by mpw on 2013-11-24
Well, interessting workaround, but no solution. As the brightness is just set to an average value. Thanks anyway, already better.

/edit: Is it possible to set brightness to 50% at boot, too?

---

### Post by mikewhatever on 2013-11-29
Not sure what you mean by 'avarage value'.  What value did you choose, and which one do you actually want?

---

### Post by mpw on 2013-11-29
I mean, after every resume it's set to 50%, as I set it like that. Is there any option to store the brightness level before standby and set it back to this level after the wakeup?

---

### Post by mpw on 2013-12-15
Hello,

did anyone of you try the cedarview graphics driver? It shall have 2D acceleration, full hd video playback and poor (by default disabled) 3d acceleration. Which is much more than the gma500_gfx driver.

Looks very good, but works only with Ubuntu 12.04.1, Xorg 1.11 and Kernel 3.2. Anyway, worth a look?

Bye
MPW

[http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/](http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/)

---

### Post by thopiekar on 2014-07-25
For the latest work on EMGD driver please take a look at [http://ubuntuforums.org/showthread.php?t=2107593](http://ubuntuforums.org/showthread.php?t=2107593) and [https://github.com/EMGD-Community/intel-binaries-linux/issues](https://github.com/EMGD-Community/intel-binaries-linux/issues) .
I provide a PPA and host all the work at GitHub. EMGD is told as being dead, but there are "just" fixes to the DRM part needed to make it work.
Finally creating good xorg.conf will make it do it smooth.
(The kernel module is currently supporting version 3.10 until 3.15 and I started on make patches for 3.16 which is release candidate)

---

### Post by mpw on 2014-07-25
Hi,

these are interessting news for me as I still use a Sony Laptop with that GMA500.

Do you have any plans to fix VAAPI? Because this is the thing that bothers me the most. I can't watch videos on that device, as the atom processor is too slow to play 720p and linux lacks of the driver capabilities to decode the video on the gpu.

Just mplayer would be amazing.

---

### Post by sang-gyegmx.de on 2014-08-21
Hi there, 

I hope it is ok to enter this thread. I started my own today ([http://ubuntuforums.org/showthread.php?t=2240671&page=2](http://ubuntuforums.org/showthread.php?t=2240671&page=2)), and it was suggested that I talk to you guys.

Issue: 
After the installation of Ubuntu on an ASUS Eee PC, the keyboard is not working in Desktop, but working fine during the installation and in terminal mode, also the CTRL SHIFT F2 combination DID work out of desktop.
When I run Ubuntu from the USB (try ubuntu) the keyboard works fine too.

Just before the system starts I get an error message :
[13.136949] gma500 0000:00:02.0: GPU: Power management timed out.
[13.640528] gma500 0000:00:02.0: trying to get vblank count for disabled pipe
[13.642461] gma500 0000:00:02.0: trying to get vblank count for disabled pipe


This led to the assumption that the GMA500 is involved in the trouble. From the earlier posts - being very new at this - I am not sure how to proceed.

Grateful for any suggestions. 

s.

---

### Post by Bashing-om on 2014-08-21
Just to say: I have subscribed to this thread in the interest of sang-gyegmx.de.

[INDENT][INDENT]where there are solutions 
[INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by thopiekar on 2014-08-22
Sorry, that I didn't take care about this thread. I just look frequently at the thread which just about the closed-source driver.

[COLOR=#000000]@sang-gyegmx.de : looks like gma500 (opensource driver) is still in use - make sure you've installed emgd-driver which will blacklist this driver for you.

@mpw: Take a look at the other thread. libVA is working with XBMC. Haven't built mplayer so far as I personally use XBMC often on my own. To get libVA working you'll need a downgrade to libva-1.0.16. The quickstart guide at github is just outdated.
[/COLOR][https://github.com/EMGD-Community/intel-binaries-linux#libva-requirements](https://github.com/EMGD-Community/intel-binaries-linux#libva-requirements)[COLOR=#000000]

Report problems with EMGD here: [/COLOR][https://github.com/EMGD-Community/intel-binaries-linux/issues](https://github.com/EMGD-Community/intel-binaries-linux/issues)[COLOR=#000000]

[/COLOR]

---

### Post by Bashing-om on 2014-08-22
@ thopiekar; Hello ;

I appreciate the response. In respect to sang-gyegmx.de, the system magically corrected the situation. I am advised he is in good shape at this time.
I have added your recommendation to my notes !

[INDENT][INDENT][INDENT]my regards
[/INDENT][/INDENT][/INDENT]

---

### Post by thopiekar on 2014-08-29
No problem. Are you working on the documentation at [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) ?
I wanted to update the EMGD instructions, but I'm not able to login to the wiki. Already contacted the webmaster, but no answer/change.

---

### Post by blugeco on 2014-08-31
Hi guys,

I just wanted to share my experience with you.
I've been trying different distros on my GMA500 netbook and by far the better working is [Manjaro Netbook]("https://forum.manjaro.org/index.php?topic=7319.0")
It has an ATOM optimised kernel, uses the gma500_gfx and has even a older version of Flash working. It uses XFCE using a sensible layout optmised for smaller screens.

mplayer works but the full screen upscaling doesn't .... but, to be honest, I don't think I have seen any distribution working fine with it on my netbook.
The only stable driver I have ever seen working with a proper full screen was the old PSB driver (available with Ubuntu Lucid and Maverick I think ...). 

cheers, 
blugeco

---

### Post by cedavis82 on 2014-09-12
Alright so I have a terrible Asus Eee PC 1101HAB thing that i have to use because my normal computer is currently being repaired, and I installed ubuntu on it thinking it would run better than windows 7 seeing as it's 32 bit and only has a gig of ram, but turn out I need some special driver. I am currently typing with an immense amount of lag due to the lack of this gma500 driver, but no one on the internet seems to know how to install it on ubuntu 14, and the ubuntu wiki page only talks about it up until ubuntu 12. 

the sudo add-apt-repository etc thing to install it works fine, until i have to say sudo apt-get install poulsbo-driver-2d, 3d, config. according to another forum, this is because i have the newest version of ubuntu? is there any way i can fix this? because it's very annoying and i can barely use this computer right now because of this problem.

---

### Post by cedavis82 on 2014-09-12
> **cedavis82 said:**
> Alright so I have a terrible Asus Eee PC 1101HAB thing that i have to use because my normal computer is currently being repaired, and I installed ubuntu on it thinking it would run better than windows 7 seeing as it's 32 bit and only has a gig of ram, but turn out I need some special driver. I am currently typing with an immense amount of lag due to the lack of this gma500 driver, but no one on the internet seems to know how to install it on ubuntu 14, and the ubuntu wiki page only talks about it up until ubuntu 12. 

the sudo add-apt-repository etc thing to install it works fine, until i have to say sudo apt-get install poulsbo-driver-2d, 3d, config. according to another forum, this is because i have the newest version of ubuntu? is there any way i can fix this? because it's very annoying and i can barely use this computer right now because of this problem.

just downgraded to 12.10, because the wiki said that it should work on ubuntu 12, but it's still lagging incredibly and i still can't do the sudo-apt-get install poulsbo-driver-2d etc. thing because it can't find poulsbo-driver-2d, 3d, nor poulsbo-config. help please.

---

### Post by cedavis82 on 2014-09-13
ok turns out this computer's just so bad i needed to use xubuntu (or rather lubuntu, just something wayyyy lighter) for it to run decently. if someone could delete these past three replies that'd be bomb.

---

