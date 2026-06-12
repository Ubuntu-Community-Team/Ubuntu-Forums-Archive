---
title: "All accounts unable to login"
date: 2009-10-26
forum: General Help
---

### Post by derbyjon on 2009-10-26
Hi everyone,

I'm currently unable to login to my Ubuntu Desktop system.

Here's a quick chronology:
1) Started last night from 8.04 that's been working fine for over a year.
2) Upgraded to 8.10 via update manager. Everything completed normally with a few prompts to replace modified configs, one of which was related to cupsys network sharing.
3) Rebooted and logged in. Everything seemed to be happy.
4) This morning, again booted and logged in, everything still seemed fine. Other computer on network unable to see printer which I half-expected due to prompt during upgrade.
5) Turned network printer sharing on and also tried printing a test page direct from the Ubuntu system just to check. It was put in print queue but message appeared asking for authentication, clicked on this and it showed a text entry box with 'none' written next to it. Tried with empty text box and also my password, neither of which worked. Googled for possible explanation, didn't find anything applicable to my scenario, so updated printer installation from Cups web interface. At the end of this it popped up a user/pwd dialogue box for authorisation (which in hindsight seems a bit odd?). Entered user/pwd after which any attempt to talk to the print server through Web interface or GUI resulted in connection error message.
6) Therefore decided to reboot assuming print server had fallen over. Following boot, unable to login via GUI or tty.

The nature of the login failure on the GUI is that after entering username & pwd the screen goes black for a couple of seconds and then returns to the login 'user' screen. No error message. On the tty, it simply redisplays the login prompt, again with no error message. Note I have also tried deliberately entering an incorrect password and on both GUI and tty it displays the expected error message. Therefore it definitely recognises my username and password.

I have also tried this using another account, and it fails in the same way.

I have tried reverting to the previous 8.04 kernel, this also fails in the same way.

My setup is to boot from /dev/sda2 which is a much older Ubuntu install. The root (/) mount point is /dev/sda4, and /dev/sda3 is mounted as /home. This has been the case for a couple of years and has worked fine.

I have booted from a 7.10 live CD. If I copy and paste the exact parameters from the /etc/fstab of the /dev/sda4, I can mount /dev/sda3 and see the user home directories fine.

Any suggestions would be much appreciated as I'm a bit stumped. It would be interesting to confirm whether /home is definitely being mounted properly as this might explain the behaviour. However I'm not sure how to check that when I cannot login from the real kernel image (or any of the old images).

Many thanks,

Jon.

---

### Post by Giblet5 on 2009-10-26
Something went very wrong during the upgrade.

I recommend that you perform a backup RIGHT NOW.

Flip to the console via CtrlAltF1.

Log in.

Save your installed packages list: ```
aptitude -F '%?p %?V' search '~i' | awk '{ print $1 }' > packages.txt
```

Use 'tar' to backup your stuff somewhere. I'll assume that you have a FAT32 Western Digital MyBook external USB disk drive connected and that it automounted to /media/MyBook: ```
sudo tar -czvpf /media/MyBook/backup.tar.gz /home
```

Then reinstall 8.10 from the 8.10 LiveCD.

Create the same username you had before.

Run update manager to patch everything. That will include a reboot.

Reinstall the backup: ```
cd /
sudo tar xzvf /media/MyBook/backup.tar.gz
cd
for i in `cat packages.txt`
do
  sudo apt-get install $i -yq
done
```

You'll have a few configurations to tweak, but that will put you pretty much where you were with 8.04, except on 8.10.

---

### Post by derbyjon on 2009-10-26
Hi Giblet5, thanks for the reply.

Just before the upgrade I rsync-ed /home to a local USB drive, so I'm not worried about losing data.

Regarding the problem I can't login via CtrlAltF1 as this fails (back to login prompt with no error).

---

### Post by Giblet5 on 2009-10-26
> **derbyjon said:**
> Hi Giblet5, thanks for the reply.

Just before the upgrade I rsync-ed /home to a local USB drive, so I'm not worried about losing data.

Regarding the problem I can't login via CtrlAltF1 as this fails (back to login prompt with no error).

Then it is already time to reinstall... :(

You can't save the packages list, but that might be a good thing in disguise (my system has a ton of stuff I never use - a reinstall would be good about now...)

We can spend a few days nailing-down what's wrong and why, but that won't tell us what *else* might be wrong...

---

