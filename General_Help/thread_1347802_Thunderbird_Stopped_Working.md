---
title: "Thunderbird Stopped Working"
date: 2009-12-06
forum: General Help
---

### Post by lyhy on 2009-12-06
Hi,

I'm running 9.04 and 2 days ago Thuderbird mysteriously stopped working for me. When I click the icon it says "Starting Thunderbird"... it hangs out for awhle... the "Starting Thunderbird" message disappears... and then... nothing!

When I do a "ps aux" I see the following: /usr/lib/thunderbird/thunderbird-bin. Unfortunately, what I don't see it the program itself.

I tried uninstalling and reinstalling and that didn't help. There is a "complete removal" option, but I am hesitant to do that because I'm worried it will delete all of my folders, emails, settings. etc.

Can someone please help me?

Thanks,
Larry

---

### Post by lidex on 2009-12-06
Probably a corrupted profile/extension. What version of Thunderbird? Did you recently install any themes or extensions?

In an Alt+F2 run dialog enter:
```
thunderbird -profilemanager
```

Create a new profile and start tbird with that.

---

### Post by lyhy on 2009-12-06
Hi,

I tried what you suggested but it didn't work. When I created a new profile it fired up the account setup wizard. I walked through that entering fake data, but when I click "finish" nothing happens.

As you can see from the output below, more process are running, but the client program is still not visible.

=================
larry@larry-desk:~$ ps aux | grep 'thunderbird'
larry     5526  0.0  0.0   1872   548 ?        S    18:06   0:00 /bin/sh /usr/bin/thunderbird
larry     5538  0.0  0.0   1872   552 ?        S    18:06   0:00 /bin/sh /usr/lib/thunderbird/run-mozilla.sh /usr/lib/thunderbird/thunderbird-bin
larry     5542 20.4  1.0  96712 33160 ?        Sl   18:06   0:01 /usr/lib/thunderbird/thunderbird-bin
=================

The weird thing is that I have a desktop running the same environment and everything works fine on that. 

To answer your other questions:

1) I have version 2.0.0.23. (At least I think I do; I can't see it; this is the version on my desktop)

2) I did not download any new themes or extensions. The only thing I may have downloaded is stuff from one of the periodic Update Manager Alerts. (And if I did, I don't remember exactly what it was because I always just install them without looking.)

Do you (or anyone) have any ideas? Like everone else I absolutely depend on having email capability. Also, I'd love to be able to solve this problem without losing all of the accounts, emails, etc. that I have set up and accumulated for about a year.

Boy, I sure hope someone can help me...

Thanks,
Larry

---

### Post by lidex on 2009-12-06
Kill all those processes and try again with profile manager. Skip the account setup part for now - just want to see if it will run.

---

### Post by lyhy on 2009-12-07
Hi lidex,

Thanks for following up. When I create a new user and click 'Start Thunderbird' nothing happens. 

I actaully did this several times yesterday - each time after rebooting to make sure I was starting with a clean slate - and "nothing" was usually what happened. The "Create Account" wizard only fired up about 10% of the time.

When I do a "ps aux" no thunderbird processes are listed.

-- Larry

---

### Post by lidex on 2009-12-07
OK. Make sure t-bird is closed. Press Alt+F2 and enter "gnome-system-monitor". Press run. If you see any t-bird processes, kill them. Open nautilus and navigate to your user directory (/home/your_username) and drill down to .mozilla-thunderbird (/home/your_username/.mozilla-thunderbird). In that directory you will see a folder with something like 8 random characters .default (98hg3g3k.default). This is your profile folder. Left-click and drag that folder into your Documents folder.

Open synaptic (system>administration>synaptic package manager). Select "installed" in left pane. In search box enter "thunderbird". Right-click on any/all packages that appear in right pane and mark for complete removal. Click "apply". Now open a terminal and run this command:
```
update-menus
``` (If you created any custom launchers for t-bird delete those as well)

Now you can re-install. Right-click the package "thunderbird" (nothing else) and mark for installation. Apply. Allow suggested/dependencies. Close everything but terminal. Re-run ```
update-menus
``` Now go to menu and start t-bird.

---

### Post by lyhy on 2009-12-08
Thanks a lot for hanging in there, lidex! My setup got so messed up with all of the things I tried (many on my own without really knowing what I was doing) that your advice and instructions were just what I needed!

Thanks agian for your help,
Larry

---

### Post by lidex on 2009-12-08
> **lyhy said:**
> Thanks a lot for hanging in there, lidex! My setup got so messed up with all of the things I tried (many on my own without really knowing what I was doing) that your advice and instructions were just what I needed!

Thanks agian for your help,
Larry

You're welcome! ;)

---

