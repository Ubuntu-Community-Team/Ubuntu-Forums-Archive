---
title: "A almost hard lock in Ubuntu 12.04."
date: 2012-06-23
forum: General Help
---

### Post by irv on 2012-06-23
First, I install Ubuntu 12.04 Alpha/Beta release back in December of last year. Tested it for bug and never once had to re-install it for any reason. It was one of the most solid releases I found yet.

I keep up with all the updates and upgrades from day one right up and to including the final release. Now it has been running flawlessly up to about 4 weeks ago. When one day it just would not respond to anything. The reason I called it a almost hard lock is because I could still move my mouse pointer and click on things but nothing would happen. I had no choice but to hit the power button and restart the computer.

Now this problem continues to happen. I am one who very seldom turns off his laptop. I will put it in suspend mode when moving from place to place or going out of town. This way when I open the lid I am right back to where I left off. This problem will happen every two to three days. Like I said this was not the case up until about 4 weeks ago.

I know I could just dump everything and re-install, but I have everything just like I want and don't want to go through the hassle of starting all over again.

My question is, is there a log file that I can look at that might tell me what is happening? If it is a app that is doing this I could remove it or re-install it.

Thanks ahead of time for the help.

---

### Post by ajgreeny on 2012-06-23
It could be worth checking the size of the system folders /tmp and /var every so often to see if they are becoming so large with log or temporary files that stop the system from operating properly.  This is possible when you have long uptimes as you will get in a system that goes into suspend or hibernate and does not shutdown very often.

An occasional ```
df -hT
``` command will tell you the overall disk use in %age terms of all mounted partitions and if any are showing higher than expected figures you can check things in more detail.

---

### Post by irv on 2012-06-23
> **ajgreeny said:**
> It could be worth checking the size of the system folders /tmp and /var every so often to see if they are becoming so large with log or temporary files that stop the system from operating properly.  This is possible when you have long uptimes as you will get in a system that goes into suspend or hibernate and does not shutdown very often.

An occasional ```
df -hT
``` command will tell you the overall disk use in %age terms of all mounted partitions and if any are showing higher than expected figures you can check things in more detail.

This is what I am seeing. But remember I just rebooted a short time ago. 
```
irv@irv-Inspiron-1521:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda7      ext4      211G   63G  138G  32% /
udev           devtmpfs  1.9G  4.0K  1.9G   1% /dev
tmpfs          tmpfs     766M  888K  765M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.9G  2.0M  1.9G   1% /run/shm
/dev/mmcblk0p1 vfat       30G  7.4G   23G  25% /media/3166-3166
/dev/sda2      fuseblk   123G   82G   41G  67% /media/123A57B13A579099
irv@irv-Inspiron-1521:~$ 

```
And this is my tmp properties 
[ATTACH]220113[/ATTACH]

---

### Post by ajgreeny on 2012-06-23
> **irv said:**
> This is what I am seeing. But remember I just rebooted a short time ago. 
```
irv@irv-Inspiron-1521:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda7      ext4      211G   63G  138G  32% /
udev           devtmpfs  1.9G  4.0K  1.9G   1% /dev
tmpfs          tmpfs     766M  888K  765M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.9G  2.0M  1.9G   1% /run/shm
/dev/mmcblk0p1 vfat       30G  7.4G   23G  25% /media/3166-3166
/dev/sda2      fuseblk   123G   82G   41G  67% /media/123A57B13A579099
irv@irv-Inspiron-1521:~$ 

```And this is my tmp properties 
[ATTACH]220113[/ATTACH]
So the disk filling up is not a problem at the moment.

Check again after a few days with no reboot, and compare the figures, then keep repeating the checks.

I may be completely wrong, of course, but it is so easy to do it is worth looking into, I think.

---

### Post by irv on 2012-06-23
Thanks for the advice. I will do this and see what happens. I will also try to see how long before it locks up again. 
It also may be when I am running some app. I will start to take notes. Maybe I can pin point it.

---

### Post by irv on 2012-07-06
After putting up with this for awhile now, and if anything, it has gotten worst. It stops responding to mouse and keyboard activities two or three times a day now. It doesn't make any difference what I am doing. I could be running a video, I could be browsing (Chrome or Firefox), it just randomly locks up. I call it a lock up, but I can still move the mouse pointer around the screen but it will not respond to any mouse clicks or keyboard input. The only choice I have is to hold down the power button until it shuts down and then do a restart. If I can't find what is causing this I will have to do a re-install. 
If any one has any ideas on what to try please let me know?
Thanks

---

### Post by irv on 2012-07-07
I gave it 24 hours. Any one have any ideas on what I can try. I would like to see if I can find an answer to why this is happening.

---

### Post by irv on 2012-07-10
It is still locking up. It seem that when I am doing something fast. Like moving the mouse or typing while something else is running. Closing a movie and trying to move on to something else it just locks up. It is happening two to three times a day now and I just can't get a handle on the problem. I could re-install, but I am trying to figure out what is causing this.

---

### Post by irv on 2012-07-17
It's been over three weeks now since I open this thread and I think I am seeing a pattern. I can cause this lockup by going to a youtube video in a Chrome browser. If I play more then one or two videos it will lock up. Now if I don't use the Chrome browser it doesn't lockup.

Now it will lockup even when I am not playing a video when I have once open the Chrome browser, but if I don't open it, it does not lockup. I believe the problem is with the Chrome browser or one of the addons.

I also notice that if you play videos with commercials when it comes back to the video the video is back and the sound keeps playing. Now this only happen in Chrome Browser and on the Chromebook which uses the Chrome browser. I believe it is a bug in the browser.

Is anyone else having this problem?

---

### Post by analogdialog on 2012-07-17
I have Ubuntu 12.04 and use chrome and watch youtube videos, no problems so far (>3 month).  Maybe it's an add on ?
You may want to reinstall chrome.

---

### Post by irv on 2012-07-17
> **analogdialog said:**
> I have Ubuntu 12.04 and use chrome and watch youtube videos, no problems so far (>3 month).  Maybe it's an add on ?
You may want to reinstall chrome.

I think I am going to try this. If this problem goes away I will post it here. May have to give it awhile to see.
Thanks

---

### Post by irv on 2012-07-17
In my case I started with doing a clean install of 12.04 Alpha 1 and then kept updating/upgrading until the finial release. And btw I never had one issue during that Alpha/beta testing time. This is the first issue that has come up. btw I did a reinstall of the Chrome Browser, and I can't get it to lockup now. Maybe I am on to something, but time will tell.

Yes I agree that doing an upgrade from an older version does cause problem sometimes. I find it easier to just do a clean install and reinstall all my apps (I keep a list of them in Ubuntuone), and I can be up and running quicker then doing an upgrade,(which take a long time if you have a lot of apps to upgrade).

Sorry I don't have an answer to your question in your post.

---

### Post by matt_symes on 2012-07-17
Hi

Is there anything in /var/log/syslog ?

Kind regards

---

### Post by irv on 2012-07-18
> **matt_symes said:**
> Hi

Is there anything in /var/log/syslog ?

Kind regards

OK, it just lockup. here is the syslog during the time of the lockup.
> Jul 18 16:00:01 irv-Inspiron-1521 CRON[9857]: (root) CMD (/usr/lib/prey/prey.sh >/var/log/prey.log)
Jul 18 16:09:01 irv-Inspiron-1521 CRON[10048]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jul 18 16:09:01 irv-Inspiron-1521 CRON[10047]: (root) MAIL (mailed 1 byte of output; but got status 0x00ff, #012)
Jul 18 16:14:13 irv-Inspiron-1521 kernel: [18342.470393] CE: hpet increased min_delta_ns to 30169 nsec
Jul 18 16:17:01 irv-Inspiron-1521 [COLOR="Red"]CRON[10208]: (root) CMD (   cd / && run-parts --report[/COLOR] /etc/cron.hourly)
Jul 18 16:20:01 irv-Inspiron-1521 [COLOR="red"]CRON[10268]: (root) CMD (/usr/lib/prey/prey.sh[/COLOR] >/var/log/prey.log)
Jul 18 16:35:12 irv-Inspiron-1521 gnome-session[2471]: Gtk-WARNING: Theme file for default has no name#012
Jul 18 16:35:12 irv-Inspiron-1521 gnome-session[2471]: Gtk-WARNING: Theme file for default has no directories#012
Jul 18 16:35:59 irv-Inspiron-1521 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jul 18 16:35:59 irv-Inspiron-1521 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="617" x-info="http://www.rsyslog.com"] start
Jul 18 16:35:59 irv-Inspiron-1521 rsyslogd: rsyslogd's groupid changed to 103
Jul 18 16:35:59 irv-Inspiron-1521 rsyslogd: rsyslogd's userid changed to 101
Jul 18 16:35:59 irv-Inspiron-1521 mtp-probe: checking bus 3, device 2: "/sys/devices/pci0000:00/0000:00:13.1/usb3/3-2"

EDIT: OK it lockup again. Look at the change in dates. It happen on the 18th so I Powered it off and turn it back on on the 19th. So the last command has some thing to do with it. This is the last thing it did when it locked: [COLOR="Red"]CRON[4916]: (root) CMD (/usr/lib/prey/prey.sh >/var/log/prey.log)[/COLOR]
> Jul 18 18:16:15 irv-Inspiron-1521 NetworkManager[961]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 18 18:16:15 irv-Inspiron-1521 NetworkManager[961]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 18 18:16:15 irv-Inspiron-1521 NetworkManager[961]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 18 18:17:01 irv-Inspiron-1521 CRON[4863]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 18 18:20:02 irv-Inspiron-1521 [COLOR="red"]CRON[4916]: (root) CMD (/usr/lib/prey/prey.sh >/var/log/prey.log)[/COLOR]
Jul 19 07:17:40 irv-Inspiron-1521 kernel: imklog 5.8.6, log source = /proc/kmsg started.

This is what is in the prey.log
> ### PREY 0.5.3 spreads its wings!
 ### Linux irv-Inspiron-1521 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

 -- Looking for connection...
 -- Got network connection!
 -- Checking URL...
 !! You need to enter your Device Key for querying the Control Panel!
 -- Cleaning up!
Any idea how to fix this?

---

### Post by matt_symes on 2012-07-19
Hi

TBH, I'm not sure what prey is. It may not even be this causing the lock up.

Maybe looking at the script file would be the way to go. 

Can you post the output of.

```
cat /usr/lib/prey/prey.sh
```As it is run via cron, stop cron as a service.

```

sudo service cron stop
```This will stop cron until a reboot and after a reboot you will need to stop cron again. Does it still freeze ? 

Kind regards

---

### Post by irv on 2012-07-19
This scrip: prey.sh

> irv@irv-Inspiron-1521:~$ cat /usr/lib/prey/prey.sh
#!/bin/bash
####################################################################
# Prey Client - by Tomas Pollak (bootlog.org)
# URL: [http://preyproject.com](http://preyproject.com)
# License: GPLv3
####################################################################

PATH=/bin:/sbin:/usr/bin:/usr/sbin:$PATH
readonly base_path=`dirname "$0"`
readonly modules_path='/var/lib/prey/modules'

####################################################################
# base files inclusion
####################################################################

. "$base_path/version"
. "/etc/prey/config"
[ ! -f "lang/$lang" ] && lang='en' # fallback to english in case the lang is missing
. "$base_path/lang/$lang"
. "$base_path/core/base"
. "$base_path/platform/$os/functions"

# if [ `number_of_instances_of prey.sh` -gt 1 ]; then
# 	log ' -- Prey is already running!'
# 	exit 1
# fi

log "${cyan}$STRING_START ### $(uname -a)${color_end}\n"

####################################################################
# lets check if we're actually connected
# if we're not, lets try to connect to a wifi access point
####################################################################

check_net_status
if [ $connected == 0 ]; then

	if [ "$auto_connect" == "y" ]; then
		log "$STRING_TRY_TO_CONNECT"
		try_to_connect
	fi

	# ok, lets check again, after waiting a bit
	sleep 5
	check_net_status
	if [ $connected == 0 ]; then
		log "$STRING_NO_CONNECT_TO_WIFI"
		if [ -f "$last_response" ]; then # offline actions were enabled
			log ' -- Offline actions enabled!'
			offline_mode=1
			get_last_response
		else
			exit 1
		fi
	fi
fi

####################################################################
# check API key and perform stuff accordingly
####################################################################

if [ $connected == 1 ]; then

	log ' -- Got network connection!'

	# we do have an API key but no device key, so let's try to add this device under the account
	if [[ -n "$api_key" && -z "$device_key" ]]; then

		log "\n${bold} >> Registering device under account!${bold_end}\n"
		self_setup

	fi

fi

####################################################################
# verify if installation and keys are correct, if requested
####################################################################

if [ -n "$check_mode" ]; then

	log "\n${bold} >> Verifying Prey installation...${bold_end}\n"
	verify_installation

	if [ "$post_method" == "http" ]; then
		log "\n${bold} >> Verifying API and Device keys...${bold_end}\n"
		verify_keys
	elif [ "$post_method" == "email" ]; then
		log "\n${bold} >> Verifying SMTP settings...${bold_end}\n"
		verify_smtp_settings
	fi

	exit $?

fi

####################################################################
# if there's a URL in the config, lets see if it actually exists
# if it doesn't, the program will shut down gracefully
####################################################################

# create tmpdir for downloading stuff, storing files, etc
create_tmpdir

if [[ $connected == 1 && -n "$check_url" ]]; then
	log "$STRING_CHECK_URL"

	check_device_status

	process_config
	process_module_config

	log "\n${bold} >> Verifying status...${bold_end}\n"
	log " -- Got status code $response_status!"

	if [ "$response_status" == "$missing_status_code" ]; then

		log "$STRING_PROBLEM"

		####################################################################
		# initialize and fire off active modules
		####################################################################

		set +e # error mode off, just continue if a module fails
		log " -- Running active report modules..."
		run_active_modules # on http mode this will only be report modules

		####################################################################
		# lets send whatever we've gathered
		####################################################################

		log "\n${bold} >> Sending report!${bold_end}\n"
		send_report

		log "\n$STRING_DONE"

	else
		log "$STRING_NO_PROBLEM"
	fi
fi

####################################################################
# if we have any pending actions, run them
####################################################################

if [ -n "$offline_mode" ]; then
	process_module_config
fi

check_running_actions

if [ "${#actions[*]}" -gt 0 ]; then
	run_pending_actions & disown -h
else
	cleanup
fi

# if on demand mode was activated, and we're not being by on demand mode itself
if [[ -z "$on_demand_call" && "$on_demand_mode" == "true" ]]; then
	enable_on_demand_mode
fi

# exit 0


---

### Post by irv on 2012-07-19
I ran the 
```
sudo service cron stop
```
and stopped the cron and then I tried to get it to lock up. So far I can't get it too.
I am not sure why cron is running as a service, I don't remember starting it. It must have started after I installed something. I will try to shut it off when I restart and see if this works, and if it does I will stop this service all together.

---

### Post by bobsan on 2012-07-19
Don't know if this addresses your problem. There seems to be some changes in Youtube in the last few days so that when you watch a Youtube video some script will try to load the html5 player and that somehow freezes Firefox. That affects not just Linux but Firefox in WIndows as well. The temporary work around is to go to [http://www.youtube.com/html5/](http://www.youtube.com/html5/) and check "leave html5 trial". I use the flashvideoreplacer addon for Firefox and always disable html5 on Youtube. I have experienced no problem with this change as long as flash is still installed (if flash is not installed then I think the script will attempt to load the html5 player even if you check the box to opt out, and freezing Firefox as a result, Flashvideoreplacer used to work even without flash installed)

See this
[http://support.mozilla.org/en-US/questions/932553](http://support.mozilla.org/en-US/questions/932553)

As someone said, there is no problem if you watch Youtube in Chrome. I am sure google would have tested their script in Chrome and made sure that it worked.

---

### Post by matt_symes on 2012-07-19
Hi

> ### PREY 0.5.3 spreads its wings!
 ### Linux irv-Inspiron-1521 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

 -- Looking for connection...
 -- Got network connection!
 -- Checking URL...
 **!! You need to enter your Device Key for querying the Control Panel!**
 -- Cleaning up! 

 Looks like quite a nifty program.

You are missing device keys for prey and you need to add them. This may help with that.

[https://groups.google.com/forum/?fromgroups#!topic/prey-security/r4Wer-IXM9U](https://groups.google.com/forum/?fromgroups#!topic/prey-security/r4Wer-IXM9U)

> I am not sure why cron is running as a service, I don't remember starting it.

cron is a standard service that runs at start up and is used to run and schedule commands. This is normal and nothing to be worried about.

I've had a look at the script you posted and it looks alright to me so i would not be worried about disabling the script as opposed to cron so you have a couple of choices now.....

1. You can either eliminate prey (almost) completely as the cause by disabling it (and re-enabling cron to run its usual tasks) for a period of time and seeing if you get the lockups 
2. You can try to configure prey straight away if you do think that is the cause of the lockups.

For option 1.

```
sudo chmod 000 /usr/lib/prey/prey.sh
```

```
sudo service cron start
```

Wait a period of time and see if you get the lockups.

If you don't get any then you will need to re-enable prey and configure it. If you do continue to get lockups then the problem is not prey.

For option 2.

Configure it correctly.

I believe you can use

 ```
/usr/lib/prey/platform/linux/prey-config.py
```

but that link above may shed more light.

The config files (again from the above link) seem to be these two...

```

/etc/prey/config
/usr/share/prey/config
```

Post back what you intend to do.

I am not entirely sure that prey is the problem though and that is why i would, personally, use option 1 first. 

Kind regards

---

### Post by thatguruguy on 2012-07-20
As an aside, have you tried ways of shutting down your computer other than simply holding the power button?

For instance, have you tried getting to a terminal by holding down the Alt+Ctrl+F1 keys? If you can get to a terminal, you can:

[LIST]
[*]run the "top" command, to see what is burning up cycles or memory, and kill that process through the "sudo killall -9 [whatever_the_process_is]" command, or
[*]restart the system by typing "sudo shutdown -r now"
[/LIST]

If you can't get to a terminal, have you tried the ["REISUB" method]("http://kember.net/articles/reisub-the-gentle-linux-restart/")? That had a MUCH lower chance of breaking something than simply killing the computer by holding down the power button.

---

### Post by irv on 2012-07-20
Well, it lockup twice this morning and that was after I ran 
```
sudo service cron stop
```
so this wasn't the problem. The good news is I just got my new SSD this morning and I am going to start fresh with a new install. Can't get any cleaner that that.
Thanks for all the help on this one, I picked up some nice tips.

---

### Post by irv on 2012-07-20
> **thatguruguy said:**
> As an aside, have you tried ways of shutting down your computer other than simply holding the power button?

For instance, have you tried getting to a terminal by holding down the Alt+Ctrl+F1 keys? If you can get to a terminal, you can:

[LIST]
[*]run the "top" command, to see what is burning up cycles or memory, and kill that process through the "sudo killall -9 [whatever_the_process_is]" command, or
[*]restart the system by typing "sudo shutdown now"
[/LIST]

If you can't get to a terminal, have you tried the ["RSEIUB" method]("http://kember.net/articles/reisub-the-gentle-linux-restart/")? That had a MUCH lower chance of breaking something than simply killing the computer by holding down the power button.
Again you been a big help on this. I printed out some info so if I have lockups again I will try this.
Thanks again

---

### Post by thatguruguy on 2012-07-20
> **irv said:**
> Again you been a big help on this. I printed out some info so if I have lockups again I will try this.
Thanks again

Not as helpful as I should have been. "sudo shutdown now" will shut down your system. to make it reboot, type "sudo shutdown -r now".

Also, there was a typo when I gave the alt+sysreq+REISUB command. I placed the "S" in the wrong place. Again, it should be REISUB, not RSEIUB as I had typed it.  It can be remembered as "Restart Even If Something's Utterly Broken".

---

### Post by irv on 2012-07-20
> **thatguruguy said:**
> Not as helpful as I should have been. "sudo shutdown now" will shut down your system. to make it reboot, type "sudo shutdown -r now".

Also, there was a typo when I gave the alt+sysreq+REISUB command. I placed the "S" in the wrong place. Again, it should be REISUB, not RSEIUB as I had typed it.  It can be remembered as "Restart Even If Something's Utterly Broken".

Actually I caught them both. I remembered the -r and I saw the typo when I went to the link.
Almost done with my backup and am getting ready to switch the drives and do the fresh install.

---

### Post by irv on 2012-07-20
I can't believe I am up and running already. It only took about 30 minutes to install and do all the updates. Even got my wireless going. Right now I am restoring all my backups. I still need to re-install all my apps, but I have a list of them in Ubuntuone. I have that all setup also. It nice to have all my emails and documents on line.

---

### Post by irv on 2012-07-21
Here we go again. Everything new and I had this same thing happen again. 
By the way the Alt+Ctrl+F1 go to a terminal and ran the sudo shutdown -r now, entered my password and nothing happen. Hit the Alt+Ctrl+F7 came back to the locked screen where nothing would work to shutdown or exit apps.
Did the Alt and SysRq key combo and went through the REISUB, and everything worked except the "B" so when I just hit the power button it went off. Restarted and everything is working again. I will try later to lock it up again.

---

### Post by matt_symes on 2012-07-22
Hi

Did you have a kernel upgrade around the time the hard locks started ?

Have you tried to boot into an old kernel and see if you still get the same lookups ?

Kind regards

---

### Post by irv on 2012-07-22
This was a fresh install on a new SSD. No problems with the install.
OK, it just happen again 20 minutes ago. Here is what I was doing. Moving the scroll bar in Chrome Browser. It seem if I try doing things to fast it will lock up. Look at the last thing in the syslog file:
> Jul 22 07:56:56 irv-Inspiron-1521 signond[2264]: signonsessioncore.cpp 832 processError 
Jul 22 07:56:56 irv-Inspiron-1521 signonpluginprocess: remotepluginprocess.cpp 523 startTask operation is completed 
[COLOR="Red"]Jul 22 07:56:56 irv-Inspiron-1521 signond[2264]: signonsessioncore.cpp 957 startNewRequest the data queue is EMPTY!!![/COLOR] 

---

### Post by matt_symes on 2012-07-23
Hi

If you can REISUB then it's less lightly to be a kernel lock up.

As for the reboot problem, have you looked at changing the grub reboot parameter ?

```
reboot=<method>
```where <method> is the rebbot method.

I'll dig out the options for you and edit this post.

EDIT:
> 
/* reboot=b[ios] | s[mp] | t[riple] | k[bd] | e[fi] [, [w]arm | [c]old] | p[ci]
   warm   Don't set the cold reboot flag
   cold   Set the cold reboot flag
   bios   Reboot by jumping through the BIOS (only for X86_32)
   smp    Reboot by executing reset on BSP or other CPU (only for X86_32)
   triple Force a triple fault (init)
   kbd    Use the keyboard controller. cold reset (default)
   acpi   Use the RESET_REG in the FADT
   efi    Use efi reset_system runtime service
   pci    Use the so-called "PCI reset register", CF9
   force  Avoid anything that could hang.
 */
 END OF EDIT.

singnond is the single sign on framework

[http://www.ubuntuupdates.org/package/webapps_preview/precise/main/base/signond](http://www.ubuntuupdates.org/package/webapps_preview/precise/main/base/signond)

I believe signond may be used by UbuntuOne.

I am not sure if this has been suggested yet but disable UbuntuOne.

Kind regards

---

### Post by jonblund on 2012-07-23
> **irv said:**
> It's been over three weeks now since I open this thread and I think I am seeing a pattern. I can cause this lockup by going to a youtube video in a Chrome browser. If I play more then one or two videos it will lock up. Now if I don't use the Chrome browser it doesn't lockup.

Now it will lockup even when I am not playing a video when I have once open the Chrome browser, but if I don't open it, it does not lockup. I believe the problem is with the Chrome browser or one of the addons.

I also notice that if you play videos with commercials when it comes back to the video the video is back and the sound keeps playing. Now this only happen in Chrome Browser and on the Chromebook which uses the Chrome browser. I believe it is a bug in the browser.

Is anyone else having this problem?

Check out:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/999910](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/999910)
and more info in: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

Many report on this problem connected to Ivy bridge. 
24 ours ago I followed the solution  in  #999910 tread and upgraded my kernel to 3.2.0-27-generic #43-Ubuntu (12.04).  
So far it looks god,  no freeze, but i am not convinced yet.
Hope this gives you some new input to your problem.

---

### Post by irv on 2012-07-23
A couple of points after reading the last two posts.
First,  jonblund I am using the same kernel you are using 3.2.0-27. I believe it update to this today.
Second, matt_symes I only have Ubuntu 12.04 and it boots right into this OS and the grub never comes up. I am not sure what rebbot method is? Quick question: how do I get the grub to come up on boot. I tried the "Ecs" key but that didn't work.
I am using ubuntuone and I am not sure how to disable it? I will try it for awhile seeing I am using the latest kernel and if I see  it lock up again I will try disabling ubuntuone.

---

### Post by jonblund on 2012-07-24
> **irv said:**
> A couple of points after reading the last two posts.
First,  jonblund I am using the same kernel you are using 3.2.0-27. I believe it update to this today.
Second, matt_symes I only have Ubuntu 12.04 and it boots right into this OS and the grub never comes up. I am not sure what rebbot method is? Quick question: how do I get the grub to come up on boot. I tried the "Ecs" key but that didn't work.
I am using ubuntuone and I am not sure how to disable it? I will try it for awhile seeing I am using the latest kernel and if I see  it lock up again I will try disabling ubuntuone.

The #999910 bug refers to" total system freeze with Ivy Bridge" only.
In my case the new kernel seems to be the solution. No freeze after two days testing.
There seems to bee more than one instability problem that can influence this behavior, maybe this can shred some light to some of them.
[http://intellinuxgraphics.org/2012.02.html](http://intellinuxgraphics.org/2012.02.html)

---

### Post by matt_symes on 2012-07-24
Hi

> rebbot

A typo. My bad. Should be been reboot method.

To change the reboot method you will need to edit the boot command line.

If you press the shift key at startup and keep it depressed you should see the GRUB menu. 

You may not have any other kernels installed though, and this may be why the GRUB menu is not displayed. 

As i said though, this may not be a kernel issue as you can REISUB and it may just be X that is hanging.

Did you disable UbuntuOne ?

Random freezes are a pain as a whole host of things can cause them from hardware to software and there is no one fix to "my computer freezes". 

The best one can do is look in the logs and hope some information is displayed there or try a binary search to eliminate different problem areas in an effort to point the problem.

My general technique is to start with hardware. eliminate dodgy hardware as the cause. I do this by running tests on the hardware such as memory tests and SMART on discs.

After that i try to see if it's X or the kernel crashing. Checking to see if the caps lock keys are flashing after the freeze. Checking the Xorg.0.* files after a lock up.

i continue like that unloading modules if it is a kernel crash or trying different kernels or trying different DE and windows managers. You can also boot into a LiveCD/USb of an older version and see if you still get the crash.

Boot into Unity 2D. Do you still get the freezes ?

Kind regards

---

### Post by irv on 2012-07-24
I am at the point where I need to let time pass to see if I get any more lockups. Before I could make my system lock by doing things very fast or keep switching videos. I tried all these things this morning and I can not get it to lockup. If it locks again I will be back to post again. But for now I am going to let some time pass and see what happens.
Thanks for all the help and the suggestions.

In closing let me say, since I installed this solid state drive and started with a fresh install of Ubuntu 12.04, it is almost hard to believe my older Dell Inspiron 1521 is running this fast. This morning when I started from a cold boot; subtracting the login time (the time it took me to type in my password) it took 15 seconds to be up and running. My wife has a Chromebook and her startup time is 7 seconds, so she is still faster, but I am very happy with my time seeing it did take me well over a minute. It isn't just the boot time, the time for loading of apps are unbelievably fast also.

---

### Post by irv on 2012-07-25
Two lockups today. Here is the syslog on the last one.
> Jul 25 16:57:49 irv-Inspiron-1521 kernel: [26157.620050] ata1: softreset failed (device not ready)
Jul 25 16:57:49 irv-Inspiron-1521 kernel: [26157.620059] ata1: applying PMP SRST workaround and retrying
Jul 25 16:57:49 irv-Inspiron-1521 kernel: [26157.792111] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 25 16:57:49 irv-Inspiron-1521 kernel: [26157.804266] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jul 25 16:57:49 irv-Inspiron-1521 kernel: [26157.814101] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
Jul 25 16:57:49 irv-Inspiron-1521 kernel: [26157.814108] ata1.00: configured for UDMA/133
Jul 25 16:57:49 irv-Inspiron-1521 kernel: [26157.828055] ata1: EH complete
[COLOR="Red"]Jul 25 16:58:51 irv-Inspiron-1521 kernel: [26219.584921] CE: hpet increased min_delta_ns to 101818 nsec[/COLOR]
Jul 25 17:01:09 irv-Inspiron-1521 kernel: imklog 5.8.6, log source = /proc/kmsg started.
Jul 25 17:01:09 irv-Inspiron-1521 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="601" x-info="http://www.rsyslog.com"] start
Jul 25 17:01:09 irv-Inspiron-1521 rsyslogd: rsyslogd's groupid changed to 103
Jul 25 17:01:09 irv-Inspiron-1521 rsyslogd: rsyslogd's userid changed to 101
The red text was the point of lockup. I think it is a kernel that is causing this.
Here is what I was doing I know Linux does not support Netflix movies, but if I try to run a Netflix video a page would come up saying my OS does not support Netflix. But this time it just locked up the computer. I am going to try this in a different browser. I will try this in firefox, I was using Chrome when this happen.

---

### Post by richpri on 2012-07-25
I am having a similar problem. Perhaps this link will give you some ideas:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1027724](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1027724)

---

### Post by irv on 2012-07-25
Thanks for the link to the bug. 

This is crazy, I tried to get it to lockup again doing the same thing and it would not do it. I tried it with firefox and Chrome and it would not lock. It just seems to be a real random thing. There is no rhyme or reason. It just seems to happen.
This was doing it on another install on a different hard drive, and now I have a new SSD installed with a clean install of Ubuntu 12.04, and it still happening. I will keep trying to pinpoint it.

---

### Post by irv on 2012-07-30
I made it three days without locking up then it locked twice. after rebooting.
Now this morning I just had it lock again this time all I was doing was typing. I checked the syslog and this was the last entire:
> Jul 30 09:48:17 irv-Inspiron-1521 signond[2248]: signonsessioncore.cpp 957 startNewRequest the data queue is EMPTY!!!  
I am seeing that "data queue is EMPTY!!!" again.

---

### Post by matt_symes on 2012-07-31
Hi

Did you disable Ubuntu One ?

Kind regards

---

### Post by irv on 2012-07-31
> **matt_symes said:**
> Hi

Did you disable Ubuntu One ?

Kind regards

No! Sorry I forgot. I am going to remove it completely and see what happens. My laptop locked up a couple of hours ago.
Will post later and let you know what happens.

Edit: This is what I removed:[ATTACH]222039[/ATTACH]

---

### Post by irv on 2012-08-01
Removing Ubuntuone didn't fix the problem. It is still locking up.

---

### Post by matt_symes on 2012-08-02
Hi

As opposed to upgrading your kernel, have you tried downgrading to the one you were using during testing when the system was stable ?

Kind regards

---

### Post by irv on 2012-08-02
> **matt_symes said:**
> Hi

As opposed to upgrading your kernel, have you tried downgrading to the one you were using during testing when the system was stable ?

Kind regards

This is a new clean install on a new SSD, and I don't remember which one I was using when I was testing. Would some of the older ones still be in the package manager? I can't check at the moment because I am using my wife's Chromebook in a gas station. I am not at home at the moment.

---

### Post by irv on 2012-08-07
I read this in wiki about Unity.
> Unity has a memory leak problem. If you use it for too long you have to restart it.

I am starting to wonder if this is my problem but watching “top” does not indicate this. I am the kind of person who does not shut off his computer but has the tendency to just let it run.

---

### Post by nomorn on 2012-08-07
I have had random hard freeze problem for quite some months too, mouse cursor was frozen every time.
Turn off the powermizer monitor in the nvidia settings and do not use the nvida temperature in conky seem to fix the random freeze problem for my system.

---

### Post by irv on 2012-08-07
> **nomorn said:**
> I have had random hard freeze problem for quite some months too, mouse cursor was frozen every time.
Turn off the powermizer monitor in the nvidia settings and do not use the nvida temperature in conky seem to fix the random freeze problem for my system.

I don't have nvida so this can't be my problem. I am thinking about just using 2D to see if it is in the compiz. 2D using metacity.

---

### Post by irv on 2012-08-09
OK, another turn of events. I tried to upgrade to 12.10 Alpha 3 last night, and it end in a disaster, so I ended up back in 12.04 with a clean fresh install again. This time I only installed a few apps that I use regularly so to not add more variables to the equation. I am going to try to run as long as I can without shutting down to see if it locks up.

Will keep you posted with results.

---

### Post by irv on 2012-08-10
Like I said above I will keep you posted on what is happening.
Well I had to restart a few time because of updates and even at that everything seemed to be running OK until today. (one day later).
I was watching some youtube videos and while switching videos it locked up again. I did the Ctrl/Alt F1 to get to a prompt and had to re-login and then ran sudo shutdown now. The computer did shutdown and when I went to power it back on it didn't want to come back on. I had to wait a few seconds and tried again still nothing. I was thinking I might have to pull the battery, but I tried holding down the power button for about 10 seconds when I let up on it, it started up again.
Now this is another fresh install and the problem is still not fixed or solved. Now I wish I didn't mark this thread solved because it isn't. I am back running again but for how long before it locks up, I don't know.

---

### Post by irv on 2012-08-11
Just another update. Since last post it locked up 3 times. All three happen when watching a video in a browser. Two were on the same video from youtube and the other was from watching my own video on Facebook.

---

### Post by irv on 2012-08-19
It's a whole new ball game now. I install Black Opal with OZ Unity Remixes. Still Ubuntu 12.04 with some special effects and extra apps. It has locked up twice, but I was fooling around with some stuff so I won't say it was the same problem.
I just checked and I have been running over 2 days now with no lockup. So with all the changes I've done It is going to be even harder to tell what was causing this so I am going to put this one to rest seeing I have it already marked as solved. Even though I don't think I really solved anything. ):P

---

### Post by RedRat on 2012-08-19
This is completely off-the-wall, but have you considered your RAM memory? These lock-ups appear to be random to some extent but seem to occur when you are doing things that have some memory demand, YouTube and Netflix. Also, you note that when you do things rapidly you can induce the lockup. Perhaps one of your memory modules has to be reseated.

---

### Post by irv on 2012-08-19
> **RedRat said:**
> This is completely off-the-wall, but have you considered your RAM memory? These lock-ups appear to be random to some extent but seem to occur when you are doing things that have some memory demand, YouTube and Netflix. Also, you note that when you do things rapidly you can induce the lockup. Perhaps one of your memory modules has to be reseated.

I couple of things I checked was the memory that was recognized in the BIOS. (4gig) and that is what I have installed. Also have been keeping an eye on memory usage when operation (running "top" in a terminal. Everything looks good: memory usage, swap usage, and CPU usage. Here is a screen shot of my top running.
[ATTACH]222900[/ATTACH]
 As you can see I am loading the processor up and have a video running in the background and everything still looks OK. I really don't think it is a memory thing.
EDIT: I should have mentioned that I have over 6gig of swap set which give me a very good cushion.

---

### Post by RedRat on 2012-08-19
> **irv said:**
> I couple of things I checked was the memory that was recognized in the BIOS. (4gig) and that is what I have installed. Also have been keeping an eye on memory usage when operation (running "top" in a terminal. Everything looks good: memory usage, swap usage, and CPU usage. Here is a screen shot of my top running.
[ATTACH]222900[/ATTACH]
 As you can see I am loading the processor up and have a video running in the background and everything still looks OK. I really don't think it is a memory thing.
EDIT: I should have mentioned that I have over 6gig of swap set which give me a very good cushion.
I was thinking that perhaps re-seating the memory modules might help here. Sometimes, when memory chips fail, they do so when heating up. Memory chips do fail and not suddenly. This is a very strange case. Not many others have reported this, I guess. This is why I think it might be hardware related. 

You have my sympathy trying to track this kind of stuff down can drive you nuts. Good luck on getting it straightened out.

---

### Post by irv on 2012-08-19
> **RedRat said:**
> I was thinking that perhaps re-seating the memory modules might help here. Sometimes, when memory chips fail, they do so when heating up. Memory chips do fail and not suddenly. This is a very strange case. Not many others have reported this, I guess. This is why I think it might be hardware related. 

You have my sympathy trying to track this kind of stuff down can drive you nuts. Good luck on getting it straightened out.

Yes memory is a funny thing. My old laptop just quit working one day and after trouble shooting it I found a bad memory chip. The brand was "Buffalo" and I contacted them and they sent me a replacement and no cost and they even paid the shipping. They said they had a lifetime warranty on their memory.
By the way that was 5 or 6 years ago and that old laptop is still running. I use it on a sound system.
EDIT: If I keep having this problem I will try reseating the memory.

---

### Post by irv on 2012-09-04
OK, it's been over two months since I started this thread. And as I remember this problem was on going for about a month before I posted this thread.
I finally exhausted things to try. I did remove all the hardware that could be removed and reseated it. Memory, hard drive, wifi card. Then did a complete diagnostics on all my hardware. And everything passed.

After locking up twice this morning I had enough. I completely wipe the hard drive (SSD) and installed Mint 13 64bit with Cinnamon desktop. Even though I really love Unity, I am going this route to see if my lockup problem goes away. If it does, then I will have to say it is something with Ubuntu with Unity 3D which uses Compiz.
Again this is still on going so I can see what happens not using Unity.

I have never had this problem with any Ubuntu release before. It still could be that my hardware does not play well with Unity.

One thing about Mint with Cinnamon that I noticed was it take 30 seconds longer to boot then Ubuntu with Unity.

---

### Post by RedRat on 2012-09-04
> **irv said:**
> OK, it's been over two months since I started this thread. And as I remember this problem was on going for about a month before I posted this thread.
I finally exhausted things to try. I did remove all the hardware that could be removed and reseated it. Memory, hard drive, wifi card. Then did a complete diagnostics on all my hardware. And everything passed.

After locking up twice this morning I had enough. I completely wipe the hard drive (SSD) and installed Mint 13 64bit with Cinnamon desktop. Even though I really love Unity, I am going this route to see if my lockup problem goes away. If it does, then I will have to say it is something with Ubuntu with Unity 3D which uses Compiz.
Again this is still on going so I can see what happens not using Unity.

I have never had this problem with any Ubuntu release before. It still could be that my hardware does not play well with Unity.

One thing about Mint with Cinnamon that I noticed was it take 30 seconds longer to boot then Ubuntu with Unity.
I hope that you have read the caveats on the Mint 13-64 Cinnamon page. Cinnamon is in the development cycle. A couple of weeks ago, I made a clean install of Mint-13-64 on my older Dell Inspiron 530n. It uses the more traditional interface, I believe they call it Maya. It boots quicker than my Ubuntu 12.04/64 on a newer HP machine. 

Since you suspect some kind of hardware interaction with the OS, I would suggest that you start more conservatively and perhaps go with the more traditional interface--at least a beta is not in the mix. If you have a freeze up now, you will not really know if it is a development problem or a real hardware interaction. 

Personally, I was not all that impressed with the Unity interface, I tried it for about month on my Ubuntu machine but did not find that it added anything real to the OS experience. I now run the Gnome Classic interface. I came at Linux from a Windows background so that might explain it. I suspect that Unity is there to attract Mac users.

---

### Post by irv on 2012-09-04
Yes, I should have install Mint 12, I used it for awhile and it seemed to run OK. It only took me about 2 hours to install 13 and get everything running. It has been running since this morning with no issues yet. Right now I am dealing with another problem. My server crashed. I had to boot with a live CD and am backing up my files. I will be trying to recover after doing this. Hopefully I won't have to do a reinstall and setup my server. I was running 10.04, and if I have to reinstall I will go to 12.04.

If I have any issues with lockups, I will drop down to Mint 12 for testing. I guess I wasn't aware that 13 was still in the beta.

---

### Post by RedRat on 2012-09-04
> **irv said:**
> Yes, I should have install Mint 12, I used it for awhile and it seemed to run OK. It only took me about 2 hours to install 13 and get everything running. It has been running since this morning with no issues yet. Right now I am dealing with another problem. My server crashed. I had to boot with a live CD and am backing up my files. I will be trying to recover after doing this. Hopefully I won't have to do a reinstall and setup my server. I was running 10.04, and if I have to reinstall I will go to 12.04.

If I have any issues with lockups, I will drop down to Mint 12 for testing. I guess I wasn't aware that 13 was still in the beta.
I think you misunderstood me. Mint 13 is released, it is only the Cinnamon gui that is in development and apparently as some issues--check out the Mint 13 page. I am running 13 on my old Dell 530n, clean install, and have not had any issues at all. It actually runs quite fast, maybe as fast at my 12.04 on my newer HP machine. Frankly, I like both of them, I switch between them trying to see which I like better. There are things I like about Mint and things I like about Ubuntu. But then I am an old fuddy-duddy and prefer the Gnome interface and not that impressed with Unity. My opinion of Unity is Meh... I suspect that it was meant to draw in Mac users.

---

### Post by irv on 2012-09-05
Redrat, 
Years ago I cut my teeth on an Atari and their operation system was developed by Digital Research and as I remember it was the same company that was working on Apple's OS. Somehow all the years I used  the ST and TT (16bit & 32bit) of Atari OS it was like using an Apple OS. Now I never got into Apple because I felt they were way over priced, and I still feel that way. Yes I am like you, I like the old Gnome 2.x desktop, but I do like the Unity also. I wanted to Alpha/Beta test 12.10 but I can't even get the live DVD to run on my Dell Inspiron 1521. (I have a bug report on this). Time will tell if it will work when the final release comes out.

The thing is I do really like 12.04 and it will be supported into 2017 and I would love to be using it but I can't because of this lockup. I am really thinking it has something to do with Compiz and using the 2D with Metacity does not cut it so I will for now use Mint 13 and wait to see what happens with Unity.

So far no lockups with Mint.

---

### Post by irv on 2012-09-05
I can't believe it just happen again using Mint. It is the same lockup. I can use the mouse and the only keys that do anything is Ctrl Alt F2 to get me to a prompt. At the prompt I can use commands.
So I run the "top" to see what is running and then found the id# of the process and used the kill to kill them. but that doesn't work either. When I use the Ctrl Alt F8 to go back to the desktop everything is still in a frozen mode. Can't do nothing. The only thing left to do is go back to the command prompt and do a 
```
sudo shutdown -r now
```
and it will shut down and reboot and then everything is working.
Let me add that when I run "top" I have memory free and I am not using any swap.
I have taken notice that everytime I lockup I am using Google Chrome Browser. So Now I am going to stop using it and see if that might be what is causing this lockup.

---

### Post by Matt 6:27 on 2012-09-05
> **irv said:**
> I can't believe it just happen again using Mint. It is the same lockup. I can use the mouse and the only keys that do anything is Ctrl Alt F2 to get me to a prompt. At the prompt I can use commands.
So I run the "top" to see what is running and then found the id# of the process and used the kill to kill them. but that doesn't work either. When I use the Ctrl Alt F8 to go back to the desktop everything is still in a frozen mode. Can't do nothing. The only thing left to do is go back to the command prompt and do a 
```
sudo shutdown -r now
```
and it will shut down and reboot and then everything is working.
Let me add that when I run "top" I have memory free and I am not using any swap.
I have taken notice that everytime I lockup I am using Google Chrome Browser. So Now I am going to stop using it and see if that might be what is causing this lockup.


What a crazy story!  I just read all six pages of this thread in hopes of a solution (thought I saw "Solved" at one point).  I'm experiencing lockups/freezes non-stop of late with 12.04.1 64bit.  I go back to Hoary & Dapper days, and I'm sorry to say this is fast becoming my least stable rendition of Ubuntu so far... and an LTS no less.  It's very frustrating for me, as I'm sure it is for you. Like you, I've thought about migrating away from Ubuntu after all these years, but your post saying Mint is doing it too may delay that. I'll try uninstalling Chromium to see if that helps... it does seem since I made Chromium my default browser, things have gone (more) awry.  I don't hit YouTube much, but watch video news on our regional TV network. Thanks for all the time you put to this, it has been instructive.

---

### Post by irv on 2012-09-06
Matt 6:27, I see you said you use Chromium, I was using Chrome which is different. But it does seem since I move away from Firefox and started using Chrome is when this lockup started. Here is another shot of "Top" running in a terminal.
[ATTACH]223755[/ATTACH]
As you can see I have been up running now for 22 hours without a lockup. I will be on the road today but I take my laptop with me so I plan on not shutting it off but will keep it in suspend mode. So far it has not locked up since I quite using Chrome.

If it runs without locking up until tomorrow, I plan on reinstalling Ubuntu 12.04 with Unity again, (Clean Install). And then running without Chrome. Then if all goes well, I plan to start using Chrome, but removing all my plugins and addons. And if it lockes up again, I will just use Firefox and not use Chrome again.

In a way I am hoping that this is the problem because I sure want to keep using Ubuntu with Unity. In a way I am glad it locked up in Mint this way I know it was not Ubuntu with Unity that was causing the problem. And I am also glad all my hardware checks out OK also.

---

### Post by rickm1945 on 2012-09-06
> **irv said:**
> Matt 6:27, I see you said you use Chromium, I was using Chrome which is different. But it does seem since I move away from Firefox and started using Chrome is when this lockup started. Here is another shot of "Top" running in a terminal.
[ATTACH]223755[/ATTACH]
As you can see I have been up running now for 22 hours without a lockup. I will be on the road today but I take my laptop with me so I plan on not shutting it off but will keep it in suspend mode. So far it has not locked up since I quite using Chrome.

If it runs without locking up until tomorrow, I plan on reinstalling Ubuntu 12.04 with Unity again, (Clean Install). And then running without Chrome. Then if all goes well, I plan to start using Chrome, but removing all my plugins and addons. And if it lockes up again, I will just use Firefox and not use Chrome again.

In a way I am hoping that this is the problem because I sure want to keep using Ubuntu with Unity. In a way I am glad it locked up in Mint this way I know it was not Ubuntu with Unity that was causing the problem. And I am also glad all my hardware checks out OK also.

I had a similar situation. I'm running Ubuntu 12.04 Precise Pangolin Unity. I was trying Cinnamon Desktop and my system would lock up and I couldn't do anything. I had to use power button to shut down. his all started one thing ata time and finally got to the point where after boot as soon as I clicked on anything it locked up. I ask in here ans Googled the symptoms to no avail.  So I logged in with Ubuntu instead of Cinnamon and I have had no problems since. I to have had to install Ubuntu 12.04 several times each time because I wanted to try a different desktop environment. I have now decided to stay with Unity and have not had an problems. I hope maybe this helps you.

---

### Post by irv on 2012-09-06
Thanks rickm1945, but right now I am running Mint with Cinnamon without running Chrome Browser, and I have been running over 25 hours now without a lockup. I am starting to pinpoint my problem. If I can run without lockup until tomorrow then I plan to do a fresh install of 12.04 and try running it without Chrome Browser. If this works, that maybe I found the problem. Will keep all posted on this.

---

### Post by hawthornso23 on 2012-09-06
This is a real saga isn't it.

I am struck by the way that the problem has persisted across reinstalls. To me that means either a hardware issue or a configuration problem.

A configuration problem would reside in the hidden configuration files in your home directory. Especially if you've been running alpha versions you can end up with configuration files that don't quite match the version of the software you have installed, which can lead to all sorts of subtle errors. If you have home on a separate partition these configuration files can even survive a complete reinstall of the system. A misconfiguration could be quite subtle. In your case it looks almost like some application is stealing keyboard and mouse focus at irregular intervals. 

To check if you have a misconfiguration issue try creating a new user and running as them for a while.  If lockups stop it could be something wrong with one of those configuration files which is causing some application to run amok.

---

### Post by Matt 6:27 on 2012-09-07
> **hawthornso23 said:**
> This is a real saga isn't it.

I am struck by the way that the problem has persisted across reinstalls. To me that means either a hardware issue or a configuration problem.

A configuration problem would reside in the hidden configuration files in your home directory. Especially if you've been running alpha versions you can end up with configuration files that don't quite match the version of the software you have installed, which can lead to all sorts of subtle errors. If you have home on a separate partition these configuration files can even survive a complete reinstall of the system. A misconfiguration could be quite subtle. In your case it looks almost like some application is stealing keyboard and mouse focus at irregular intervals. 

To check if you have a misconfiguration issue try creating a new user and running as them for a while.  If lockups stop it could be something wrong with one of those configuration files which is causing some application to run amok.


For me, I've not used Alphas and still see issues. My hardware has passed testing, so it does appear to be a resource/config issue.  I like the idea of creating a new user for testing... thanks for the thought.

BTW: Irv, could you remove "Solved" from the tag line, as it clearly isn't.  Thanks!

---

### Post by Matt 6:27 on 2012-09-07
> **Matt 6:27 said:**
> For me, I've not used Alphas and still see issues. My hardware has passed testing, so it does appear to be a resource/config issue.  I like the idea of creating a new user for testing... thanks for the thought.

BTW: Irv, could you remove "Solved" from the tag line, as it clearly isn't.  Thanks!

Follow up:  I'm having the same issues whether logged in as Guest or a completely new user.  Re-installing now.

---

### Post by hawthornso23 on 2012-09-08
Do you have a USB headset? I've read of some types of USB headsets sometimes interfering with mouse click events.

---

### Post by irv on 2012-09-08
As I said earier I will keep all posted on my progress with this issue.
Here is the good news.
I believe I have the problem pin pointed. I quite using Chrome Browser 4 days ago and I have not had one lockup since. I want to give it a few more days, and then I am going to reinstall it and then uninstall all the extras I have running in it and see if the bare browser will lockup.
I am going to leave this thread marked as [COLOR="Red"][SIZE="3"]solved[/SIZE][/COLOR] because I believe it is.

One more point, I am back to running Ubuntu 12.04 with Unity. I did another clean Install yestereday morning. One thing I took note of was the fact that it only took about 20 minutes to do the install. I went from Mint 13 to Ubuntu 12.04 and I am wondering it keep some files because it went so fast. I took it to use the whole HD and it be the only OS. That is what it did. It is back to booting up in 20 seconds.

---

### Post by Matt 6:27 on 2012-09-08
> **irv said:**
> As I said earier I will keep all posted on my progress with this issue.
Here is the good news.
I believe I have the problem pin pointed. I quite using Chrome Browser 4 days ago and I have not had one lockup since. I want to give it a few more days, and then I am going to reinstall it and then uninstall all the extras I have running in it and see if the bare browser will lockup.
I am going to leave this thread marked as [COLOR="Red"][SIZE="3"]solved[/SIZE][/COLOR] because I believe it is.

One more point, I am back to running Ubuntu 12.04 with Unity. I did another clean Install yestereday morning. One thing I took note of was the fact that it only took about 20 minutes to do the install. I went from Mint 13 to Ubuntu 12.04 and I am wondering it keep some files because it went so fast. I took it to use the whole HD and it be the only OS. That is what it did. It is back to booting up in 20 seconds.


Fair enough re the status.  I too reinstalled 12.04.1 64bit, sans the Chromium, and to date am having no issues.  I don't boot nearly as fast (don't have SSD yet), but am using Unity and mouse, keyboard, Dash and HUD all seem to be working normally.  I'm adding one app at a time and running the system through the paces for a bit before adding more.  Glad to read you're back in the game.

---

### Post by irv on 2012-09-08
Yes Matt 16:27 sometime it is slow going when you are trying to isolate a problem. (By the way, like your handle. I think it had something to do with being short, or am I reading something into it).
I have loaded other software, but have stay away from Chrome for now. I haven't even installed it yet. To be honest with you I really like it better then Firefox, but if it locks up what good is it. Hopefully when I start to trouble shot it, maybe I will find the problem with an addon. Time will tell.

---

### Post by irv on 2012-09-10
Alright, been running 3 days 6 hours without a lockup. Time to install Chrome browser and remove addons and see what happens.
[ATTACH]223990[/ATTACH]

---

### Post by Rader on 2012-09-11
I'm experiencing something somewhat similar -- unity "freezes" so that the mouse moves, but one can't select anything.  Going into the tty1 terminal (ctl-alt-F1), and logging in, I find that compiz is running flat out ( I use "top").  Using the proc id displayed in top, I can then use a "sudo kill -9 <procid>", which removes the compiz program.  (At this point I'm not in X, so it isn't reloaded automatically.)

Then issue "sudo service lightdm restart" to restart X (and compiz).

That gets me around the "freeze".  It is happening to me every time I invoke the "/usr/bin/vi" editor; for a while I kept trying to "vi compiz-bug" and it would freeze ... as though some intelligence was trying to prevent me from documenting what I was seeing :-)  I can't imagine yet what the problem is, but the fact that your trouble is with chrome is certainly interesting to me.

---

### Post by irv on 2012-09-11
> **Rader said:**
> I'm experiencing something somewhat similar -- unity "freezes" so that the mouse moves, but one can't select anything.  Going into the tty1 terminal (ctl-alt-F1), and logging in, I find that compiz is running flat out ( I use "top").  Using the proc id displayed in top, I can then use a "sudo kill -9 <procid>", which removes the compiz program.  (At this point I'm not in X, so it isn't reloaded automatically.)

Then issue "sudo service lightdm restart" to restart X (and compiz).

That gets me around the "freeze".  It is happening to me every time I invoke the "/usr/bin/vi" editor; for a while I kept trying to "vi compiz-bug" and it would freeze ... as though some intelligence was trying to prevent me from documenting what I was seeing :-)  I can't imagine yet what the problem is, but the fact that your trouble is with chrome is certainly interesting to me.
If you read earlier post of mine I thought compiz was my problem also, but it really turned out to be chrome. Now I reinstalled Chrome and removed all my extensions except for these three:
[ATTACH]224035[/ATTACH]
and it seems to be running OK. No lockups yet. Again, time will tell.
Hope you get to the bottom of your lockups. Are you using Chrome?

---

### Post by irv on 2012-09-13
Ran for almost 2 days and then started to lockup again, but only when using Chrome. I am just going to have to stay away from Chrome Browser. I am using Chrome browser with Ubuntu 10.04 on an older desktop and it works OK, It must be either 12.04 or something to do with my hardware and or in combination with 12.04. At least I know what is locking it up (that is Chrome browser). 

Also want to mention that it is when I am running videos in the browser is when it locks up. I know that Chrome has it's own version of Flash built in, and that could be where the problem might be.

---

### Post by krishna.988 on 2012-09-14
> **irv said:**
> Ran for almost 2 days and then started to lockup again, but only when using Chrome. I am just going to have to stay away from Chrome Browser. I am using Chrome browser with Ubuntu 10.04 on an older desktop and it works OK, It must be either 12.04 or something to do with my hardware and or in combination with 12.04. At least I know what is locking it up (that is Chrome browser). 
 
Also want to mention that it is when I am running videos in the browser is when it locks up. I know that Chrome has it's own version of Flash built in, and that could be where the problem might be.
 
 
Don't waste your time over this..as I experienced similar lockups with Ubuntu sometime earlier with the same Dell Inspiron 1521 laptop. And when I installed Windows 7 it worked smoothly.. And finally I got to know it was because of driver issue.. opensource drvers are buggy at times..:P

---

### Post by irv on 2012-09-14
> **krishna.988 said:**
> Don't waste your time over this..as I experienced similar lockups with Ubuntu sometime earlier with the same Dell Inspiron 1521 laptop. And when I installed Windows 7 it worked smoothly.. And finally I got to know it was because of driver issue.. opensource drvers are buggy at times..:P

In my case if it is drivers, then why does everything work great except Chrome Browser? I have been using Ubuntu on this Laptop since I purchase it back in 2008 and this is the first time I have had a lockup problem like this. And I have been running Ubuntu on it since then. I started with 8.04 back then.

---

### Post by Matt 6:27 on 2012-09-14
> **irv said:**
> In my case if it is drivers, then why does everything work great except Chrome Browser? I have been using Ubuntu on this Laptop since I purchase it back in 2008 and this is the first time I have had a lockup problem like this. And I have been running Ubuntu on it since then. I started with 8.04 back then.

Agreed re your driver response, since I had similar issues with completely different hardware.  I've elected to forego Chromium (in my case) and to date have not experienced any mouse or system lockups.  Still slowly adding my old apps back and, as noted, no issues to report.

---

### Post by Rader on 2012-09-14
> **irv said:**
> If you read earlier post of mine I thought compiz was my problem also, but it really turned out to be chrome. Now I reinstalled Chrome and removed all my extensions except for these three:
[ATTACH]224035[/ATTACH]
and it seems to be running OK. No lockups yet. Again, time will tell.
Hope you get to the bottom of your lockups. Are you using Chrome?
I do not have Chrome installed.  FWIW my lockups always happen when I invoke vi ...
very reproducible.

---

### Post by irv on 2012-09-15
> **Rader said:**
> I do not have Chrome installed.  FWIW my lockups always happen when I invoke vi ...
very reproducible.

It sounds like your problem is different then mine. Your's has something to do with the app vi. Is vi a text editor? I use gedit for my editing. As I remember vi is a command type editor.

---

### Post by Rader on 2012-09-15
> **irv said:**
> It sounds like your problem is different then mine. Your's has something to do with the app vi. Is vi a text editor? I use gedit for my editing. As I remember vi is a command type editor.
I tried gedit with similar results -- the X freeze happened when the file was saved.  I also saw an X freeze when invoking dolphin.

---

### Post by irv on 2012-09-15
> **Rader said:**
> I tried gedit with similar results -- the X freeze happened when the file was saved.  I also saw an X freeze when invoking dolphin.

I am starting to think you are seeing a video card issue. It could be in the driver you are using for you video card. What I would do  is start a new thread and give a description of the problem and include your video card information. To find out what your video card is, just type this command in a terminal.
```
lspci
```
Then look for your video card information.

---

### Post by irv on 2012-09-19
New problem. It is not just Chrome. I am seeing lockups in. No matter what browser I use it locks up, but only if I run a video. While running a video or after I have run a video I am getting lockups again. Now after I run a video in a browser and I shut down the browser windows and then start it back up again I don't get the lockup. This is very strange. It has something to do with software to run videos. I believe it must have something to do with flash. That is what all the browsers have in common with running videos. 

After posting this I will need to shut down this browser or it will lockup, at least that is the pattern I am seeing. 

I am going to keep using Ubuntu 12.04, because the problem is not the OS as far as I can tell.

---

### Post by RedRat on 2012-09-19
> **irv said:**
> New problem. It is not just Chrome. I am seeing lockups in. No matter what browser I use it locks up, but only if I run a video. While running a video or after I have run a video I am getting lockups again. Now after I run a video in a browser and I shut down the browser windows and then start it back up again I don't get the lockup. This is very strange. It has something to do with software to run videos. I believe it must have something to do with flash. That is what all the browsers have in common with running videos. 

After posting this I will need to shut down this browser or it will lockup, at least that is the pattern I am seeing. 

I am going to keep using Ubuntu 12.04, because the problem is not the OS as far as I can tell.

Have you tried running Opera? I have found that sometimes Opera seems to run and handle web pages slightly better than FF or Chrome. Might also be true of Flash in Opera.

---

### Post by irv on 2012-09-19
I installed Opera and will give it a try also. The next time I watch a video I will use opera and see if it locks up.

---

### Post by krishna.988 on 2012-09-19
> **irv said:**
> New problem. It is not just Chrome. I am seeing lockups in. No matter what browser I use it locks up, but only if I run a video. While running a video or after I have run a video I am getting lockups again. Now after I run a video in a browser and I shut down the browser windows and then start it back up again I don't get the lockup. This is very strange. It has something to do with software to run videos. I believe it must have something to do with flash. That is what all the browsers have in common with running videos. 

After posting this I will need to shut down this browser or it will lockup, at least that is the pattern I am seeing. 

I am going to keep using Ubuntu 12.04, because the problem is not the OS as far as I can tell.


How often does it happen? While watching a flash video or after watching it?

---

### Post by irv on 2012-09-20
> **krishna.988 said:**
> How often does it happen? While watching a flash video or after watching it?

It varies, sometime it will lockup just a short time into the video and other times I can watch a whole video and will be doing something else and it will lockup. If I don't watch any videos in a browser my laptop will run for days with no problems.

Now if I watch a video with no problems and then close out the browser and restart it I will not have a lockup. But if I watch a video and not close the browser sometime it might take an hour or two and I will lockup. You see I am looking for a pattern here.

---

### Post by krishna.988 on 2012-09-20
> **irv said:**
> It varies, sometime it will lockup just a short time into the video and other times I can watch a whole video and will be doing something else and it will lockup. If I don't watch any videos in a browser my laptop will run for days with no problems.

Now if I watch a video with no problems and then close out the browser and restart it I will not have a lockup. But if I watch a video and not close the browser sometime it might take an hour or two and I will lockup. You see I am looking for a pattern here.

Is it something to do with hardware acceleration??

---

### Post by irv on 2012-09-20
> **krishna.988 said:**
> Is it something to do with hardware acceleration??

I am not sure. Today I have been running videos in Opera Web Browser have not shut it down and it has been running all day without a lock up. It's been up almost 10 hours now. I plan on running all night in suspend mode without shutting down Opera to see what happens tomorrow.

---

### Post by krishna.988 on 2012-09-21
> **irv said:**
> I am not sure. Today I have been running videos in Opera Web Browser have not shut it down and it has been running all day without a lock up. It's been up almost 10 hours now. I plan on running all night in suspend mode without shutting down Opera to see what happens tomorrow.

Strange!!  Not able to zero down the issue..is it flash or browser or something else..lets' wait for some time.. 

Is there any way you could remove the thread from being marked as Solved..As it will grab more attention!!

---

### Post by irv on 2012-09-21
> **krishna.988 said:**
> Strange!!  Not able to zero down the issue..is it flash or browser or something else..lets' wait for some time.. 

Is there any way you could remove the thread from being marked as Solved..As it will grab more attention!!

I believe only a Mod can do that. I don't see a way I can remove it.
[COLOR="Red"]EDIT: I was wrong, I removed the solved from this thread.
[/COLOR]
Another quick update: Even after running some videos yesterday in Opera I have not had a lockup. I have been running 19 + hours now.
[ATTACH]224459[/ATTACH]
But I have to do a restart because I did some up dates this morning.
[ATTACH]224460[/ATTACH]
That means I will have to shutdown Opera and start all over again.

---

### Post by krishna.988 on 2012-09-21
> **irv said:**
> I believe only a Mod can do that. I don't see a way I can remove it.

Another quick update: Even after running some videos yesterday in Opera I have not had a lockup. I have been running 19 + hours now.
[ATTACH]224459[/ATTACH]
But I have to do a restart because I did some up dates this morning.
[ATTACH]224460[/ATTACH]
That means I will have to shutdown Opera and start all over again.

You said this happens only with chrome right or firefox also??

---

### Post by irv on 2012-09-21
> **krishna.988 said:**
> You said this happens only with chrome right or firefox also??

Yes, so far with Chrome, Chromium, and FF. I have not got it to lockup with Opera as of yet, but sometimes it takes a couple of days for me to get it to lock and other times it's only a few minutes. But I do have it pin pointed to when or after I run videos in a browser and only if I don't shut down the browser. It has been awhile since it locked up, but I haven't been running any of the browser I mentioned.

---

### Post by BlinkinCat on 2012-09-21
say - I like the look of your hometown irv - ):P

---

### Post by irv on 2012-09-21
> **BlinkinCat said:**
> say - I like the look of your hometown irv - ):P

When you look at photo 3 on the main page, right next to the eagle center you can see some new condos they just built, my house is right on the other side of them. And Photo 5 looking at the bridge you can't see my house but it is right by the bridge.

EDIT: I never notice but my house is in the banner.
[ATTACH]224472[/ATTACH]

---

### Post by krishna.988 on 2012-09-21
> **irv said:**
> Yes, so far with Chrome, Chromium, and FF. I have not got it to lockup with Opera as of yet, but sometimes it takes a couple of days for me to get it to lock and other times it's only a few minutes. But I do have it pin pointed to when or after I run videos in a browser and only if I don't shut down the browser. It has been awhile since it locked up, but I haven't been running any of the browser I mentioned.

I think your system is getting heated up since you are keeping it on for long time..may be the fan has some issue..pls check once..nothing to do with software I guess..

---

### Post by irv on 2012-09-21
> **krishna.988 said:**
> I think your system is getting heated up since you are keeping it on for long time..may be the fan has some issue..pls check once..nothing to do with software I guess..

I checked that and it is not the fan or the temp.
This is my normal reading.
> Adapter: Virtual device
temp1:        +50.5°C  (crit = +95.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +47.0°C  
Core0 Temp:   +49.0°C  
Core1 Temp:   +50.0°C  
Core1 Temp:   +42.0°C

Even when I play a video the temp does not get so high that it will lockup. One time on a desktop I had the fan came loose from the CPU it over heated and shutdown. But this is not the case here.
Thanks for the thought on this. This could have been the case if I didn't check it.

---

### Post by ortermagic on 2012-09-21
I am getting the same problem with my set-up Irv  It's been happening for several months now. I have got the most recent Firefox,  AMD Phenom 11 X2 545 processor,  Sapphire Radeon HD 6800 graphics card, just the same as you my machine will freeze then hang I am able to move mouse cursor but it will not respond to a clicky of any kind. It also goes black screen for a while, then reloads the page but whenever it does restore there is still no clicky action, it might do this several times. 

All I seem to be able to do is hold down my stop button to kill the processes and then reboot. Usually the system comes back on in a working condition, then it might be workable for anything from 10 minutes (say) up to a few days.

 Its odd and very annoying, more often it will happen whilst I'm simply browsing, I don't think it's any specifically video oriented.
 I am using the proprietary open  source driver since I've had all kinds of problems with  the amdcccle drivers which do not seem to interpret the splash screen fonts well.
I have a feeling it is possibly a 12.04  bug   :???:

---

### Post by irv on 2012-09-21
> **ortermagic said:**
> I am getting the same problem with my set-up Irv  It's been happening for several months now. I have got the most recent Firefox,  AMD Phenom 11 X2 545 processor,  Sapphire Radeon HD 6800 graphics card, just the same as you my machine will freeze then hang I am able to move mouse cursor but it will not respond to a clicky of any kind. It also goes black screen for a while, then reloads the page but whenever it does restore there is still no clicky action, it might do this several times. 

All I seem to be able to do is hold down my stop button to kill the processes and then reboot. Usually the system comes back on in a working condition, then it might be workable for anything from 10 minutes (say) up to a few days.

 Its odd and very annoying, more often it will happen whilst I'm simply browsing, I don't think it's any specifically video oriented.
 I am using the proprietary open  source driver since I've had all kinds of problems with  the amdcccle drivers which do not seem to interpret the splash screen fonts well.
I have a feeling it is possibly a 12.04  bug   :???:
When you lockup can you press [Ctrl][Alt][F2]? I can and it will take you to a prompt where you can login and then type
```
sudo shutdown -r now
```
the computer shutdown proper and come back up without just hitting the power button. This way you will not corrupt something.
Just for the record it's been two full days since my last lockup.

---

### Post by ortermagic on 2012-09-21
<code>When you lockup can you press [Ctrl][Alt][F2]? I can and it will take you to a prompt where you can login and then type</code>

Thank you for that tip Irv. Next time a lockdown/up happens happens I will try it. Do I have to enter the command using sudo as if I were doing it in a terminal?
I must admit I struggle with commands due to the fact that my 68 year old memory tends to drop out a bit these days. I will let you know how I get on with that as and when it occurs.
So far (after innumerable force quits) I have not noticed any damage, may be I've been lucky, I had two instances today, but at the moment all's well.

Sorry about the follow up post below

---

### Post by ortermagic on 2012-09-21
> **ortermagic said:**
> When you lockup can you press [Ctrl][Alt][F2]? I can and it will take you to a prompt where you can login and then type
Thank you for that tip Irv. Next time a lockdown/up happens happens I will try it. Do I have to enter the command using sudo as if I were doing it in a terminal?
I must admit I struggle with commands due to the fact that my 68 year old memory tends to drop out a bit these days. I will let you know how I get on with that as and when it occurs.
So far (after innumerable force quits) I have not noticed any damage, may be I've been lucky, I had two instances today, but at the moment all's well.

I'm not sure how to post a selected quote

---

### Post by blortuga on 2012-09-22
Instrumentation and logging can often be a big help. 

If you're a conky user, you can set it up to monitor cpu and temperature, and things like that. but then you would need to keep your desktop clear so you can see the monitors' state when it hangs.  

Another useful tool is sysstat. (usualy more useful for things like server monitoring). 

Install it thusly: 
sudo apt-get install sysstat 

sudo crontab -e 
add the following: 
*/5 * * * * /usr/lib/sysstat/sa1 
0     * * * * /usr/lib/sysstat/sa2 -A 

(there are other ways to collect data with sar) 
 and save the file.

 Cron will fire off the sysstat task every 5 minutes to dump system information into /var/log/sysstat/sa*    

You can go into /var/log/sysstat, and run the command: sar to get the cpu utilization over the time period that has been logged.  

sar -f  
will give you information for a specific date range, (which you can determine by looking at the /var/log/sysstat/* file dates).  

sar -m ALL 
will give you power-management information;  (fans, temp, cpu freq, etc.) 

sar -I ALL  
will give you Interrupt information;

 Either of these might be helpful in diagnosing.  Though a 5-minute capture window may be too coarse to give you enough information to go by (the problem may occur too quickly between captures to be logged).  It's probably not going to write state to disk after the hang, if it's a complete freeze. But if there's a situation that builds up prior to the hang, you might be able to spot the trend.  

Another thing you might try doing is running sshd, and trying to remote login (ssh) to your system AFTER the freeze, and verify whether it's just the display and video that are frozen, or if it's the whole thing.  (similar to ctrl-alt-f2).

---

### Post by krishna.988 on 2012-09-22
@IRV Did you have this issue ocuuring in Old releases of ubuntu? If not stick with the old release 11.10 or something..

---

### Post by irv on 2012-09-22
> **ortermagic said:**
> Thank you for that tip Irv. Next time a lockdown/up happens happens I will try it. Do I have to enter the command using sudo as if I were doing it in a terminal?
I must admit I struggle with commands due to the fact that my 68 year old memory tends to drop out a bit these days. I will let you know how I get on with that as and when it occurs.
So far (after innumerable force quits) I have not noticed any damage, may be I've been lucky, I had two instances today, but at the moment all's well.

I'm not sure how to post a selected quote

Yes you need to use sudo to shutdown. I have powered off a few time but there is always that chance that something not close and cause problems. 
A side note: my 74 year old mind isn't as sharp as it use to be.
> To post a quote just select the text you want to quote and then click on the quote icon.
[ATTACH]224527[/ATTACH]
I started this post last night, but my Internet went down. It has been up and down all day today. So I just went to bed and finish it this morning. So Good morning world.

---

### Post by ortermagic on 2012-09-22
@Irv, Thanks a lot Sir, It surely is weird that it's only since precise  came along that this happens. I've now subscribed to this post so I can  keep an eye on it.

@Blortuga, I have noted your comments and will  see if I can set up a diagnostic tool, it seems like a good idea,  however I have never come across the sysstat app you have indicated  seems to me there's another massive(for me)learning curve therein but I  am so curious that I will probably try it.
I have heard of and looked  into conky, never tried it. I will do some research to see if I can  find out how to get sysstat going. I have a problem in that on boot I  get a text banner for a few seconds informing me that the temp sensor is  'unreliable' which might be problematic for me.

@Irv ...there I was thinking I was one of the grandpas pogoing around with the kid's,
Seems your problem is my problem and my problem is your'n,  lol

@Krishna,  I don't want to revert to an earlier distro since I have gotten quite fond of Unity.

---

### Post by irv on 2012-09-22
I also like Unity and really like the release of Ubuntu 12.04.
Let me give you some advice on conky. here is a nice Tutorial 
[ubuntuforums.org/showthread.php?t=1010741&page=1]("ubuntuforums.org/showthread.php?t=1010741&page=1")
And here is another:
[http://ubuntuforums.org/showthread.php?t=1771033]("http://ubuntuforums.org/showthread.php?t=1771033")
You will most likely have to change some of the script to fit your system.
Here is my conky running on my desktop. It monitors my system so it might help me see what might be happening when it locks. The only problem I am having now is my system is not locked up for over 3 days now.
[ATTACH]224533[/ATTACH]
I am even back to using Firefox an Chrome.
I have had some kernel updates lately and maybe, just maybe something got fixed. Keeping my fingers crossed.
EDIT: I changed my desktop wall paper so my conky colors would match better, and besides it is getting on to fall.
[ATTACH]224540[/ATTACH]

---

### Post by irv on 2012-09-25
It been awhile since I posted an update. It been 5+ days since a lockup. I have been using three different browser. Chrome, FF, and Opera. Been watching videos in all three with no issues. I am starting to believe my lockup problem has gone away. I will give it another week and if it doesn't lockup I will mark this thread solved. I had it marked solved ones but had to remove it. Only time will tell.

---

### Post by ortermagic on 2012-10-01
Hi I am back ...problem with lockup persists, most recently I applied Irv's technique to shut down after lockup whilst watching a streamed football match, when I entered my sudo id details it locked and presented me with the following information...

[13924.224114] radeon 0000:01:00.0: gpu lockup cp stall for more than 10020 m sec

Does that mean anything to any one? 
Prior to this instance I haven't had too many lockups in the last few days.

---

### Post by RedRat on 2012-10-01
> **ortermagic said:**
> Hi I am back ...problem with lockup persists, most recently I applied Irv's technique to shut down after lockup whilst watching a streamed football match, when I entered my sudo id details it locked and presented me with the following information...

[13924.224114] radeon 0000:01:00.0: gpu lockup cp stall for more than 10020 m sec

Does that mean anything to any one? 
Prior to this instance I haven't had too many lockups in the last few days.
That sound like a graphics driver problem. If you can, try replacing your graphics card from a friend and see if that happens. How old is your graphics card? They still make the Radeon?

---

### Post by ortermagic on 2012-10-02
> **RedRat said:**
> That sound like a graphics driver problem. If you can, try replacing your graphics card from a friend and see if that happens. How old is your graphics card? They still make the Radeon?

Thanks for the input Red...I have a reasonably competent graphics card (i think), it's a sapphire Radeon HD 6870 1gb 256 bit. At the moment I am using the open source driver, because the proprietary one does not work properly on my system. Today I stripped the graphics card down and reseated the processor on it, I have just got it running again, It seems to be a totally random lockup sometimes it occurs when there is very little load at other times it might happen when i've got a lot going on? I will have to wait till it happens again.I will also have to study all the previous posts again, in case I missed something.
  I will  get conky working when I have more time and apply [COLOR=DarkOrange]@Blortugas[/COLOR] suggestion to install sysstat, asap
[B]
[/B]

---

### Post by krishna.988 on 2012-10-02
> **ortermagic said:**
> Thanks for the input Red...I have a reasonably competent graphics card (i think), it's a sapphire Radeon HD 6870 1gb 256 bit. At the moment I am using the open source driver, because the proprietary one does not work properly on my system. Today I stripped the graphics card down and reseated the processor on it, I have just got it running again, It seems to be a totally random lockup sometimes it occurs when there is very little load at other times it might happen when i've got a lot going on? I will have to wait till it happens again.I will also have to study all the previous posts again, in case I missed something.
  I will  get conky working when I have more time and apply [COLOR=DarkOrange]@Blortugas[/COLOR] suggestion to install sysstat, asap
[B]
[/B]

Check how it works in Windows(hope you are dual booting windows) with the driver installed from the site..This way it confirms whether it is the graphics card which is creating the problem.

---

### Post by irv on 2012-10-02
> **ortermagic said:**
> Hi I am back ...problem with lockup persists, most recently I applied Irv's technique to shut down after lockup whilst watching a streamed football match, when I entered my sudo id details it locked and presented me with the following information...

[13924.224114] radeon 0000:01:00.0: gpu lockup cp stall for more than 10020 m sec

Does that mean anything to any one? 
Prior to this instance I haven't had too many lockups in the last few days.

Many PC's today have diagnostic utility built in. When you first boot your PC there might be a key combo you can press to go into diagnostic mode. When I start having lockups I ran a check on my system and all my hardware checked OK. 
Also I would remove the graphic card and blow out the slot, clean the contacts and reseat the card.

Just one quick update on my lockup. It's been over 2 weeks now so I am thinking what ever my problem was it seems to have gone away. Have done a kernel update so maybe that was the problem.

---

### Post by RedRat on 2012-10-02
> **ortermagic said:**
> Thanks for the input Red...I have a reasonably competent graphics card (i think), it's a sapphire Radeon HD 6870 1gb 256 bit. At the moment I am using the open source driver, because the proprietary one does not work properly on my system. Today I stripped the graphics card down and reseated the processor on it, I have just got it running again, It seems to be a totally random lockup sometimes it occurs when there is very little load at other times it might happen when i've got a lot going on? I will have to wait till it happens again.I will also have to study all the previous posts again, in case I missed something.
  I will  get conky working when I have more time and apply [COLOR=DarkOrange]@Blortugas[/COLOR] suggestion to install sysstat, asap

Believe it or not, graphics cards can crap out! I had that happen on the video card that came on my grandson's HP Pavilion, of course after the warranty expired. Replaced it with a new Nvida card. Quite a few years ago when building my older computer, the graphics card that I bought had a capacitor fall off as I picked it up! You know what happens. This is why I suggested borrowing someone else's graphic card and trying it out if possible.

---

### Post by ortermagic on 2012-10-02
I did disassemble my graphics card, clean it up and re-seat it.
I'm now waiting to see if it's  still gonna be a problem. In the meantime I have to get some sort of conky going. I am also giving amdcccle another go in case it's a driver related thing.
The graphics card looked dusty, but fairly healthy(no blown caps or scorch marks). 
I will continue to investigate this strange phenomenon !

---

### Post by irv on 2012-10-07
I think this is going to be my last post here seeing it been about 3 weeks + since my last lockup. Everything is really running great now.
[ATTACH]225248[/ATTACH]

---

### Post by ortermagic on 2012-10-08
> **irv said:**
> I think this is going to be my last post here seeing it been about 3 weeks + since my last lockup. Everything is really running great now.
[ATTACH]225248[/ATTACH]
Thanks for your help Irv, especially for drawing my attention to (sudo shutdown -r now)thats been a great help. Something seems to have happened here as well since I too am getting fewer lockups of late.
I'm now concentrating on getting a respectable conky installed, maybe our paths will cross again.
Be good!

---

### Post by vkadal on 2012-10-08
There may be hardware failure. I also had unusual behavior like yours and finally found my RAM was faulty. After replacing the same I found the problem was solved

---

