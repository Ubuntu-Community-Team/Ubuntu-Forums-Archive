---
title: "Can't boot ubuntu - need to mount encrypted partition"
date: 2010-05-02
forum: General Help
---

### Post by erickim on 2010-05-02
Hello,

Times like this Ubuntu makes me want to pull my hair out. 

When I enter my pass on the login screen, it brings up a "Could not update ICEauthority file" error and then goes to a black screen. I've tried to fix this problem for the past 2-3 hours (searching google, these forums, etc) and at this point, I just want the data off my drive so I can restart with a fresh install of Ubuntu.

I used the "gsku nautilus" command to mount the disk from a Ubuntu Drive boot, but it's not letting me have access to the encrypted drive. Does anyone know of a work around for this?


Thanks!

---

### Post by jstalnak on 2010-05-04
What you're running into is a file system that must be mounted *before* you login. The ICEauthority data is written at login time to your home directory and as things now are, that directory is not 'there' for writing. I'm in the same boat :-)

I have an encrypted filesystem that I mount as /home. But my Lucid upgrade required that I do a clean install and that wiped out my /etc/crypttab and /etc/fstab, and the keyfiles I used to automatically mount the filesystem. I'm having to redo them manually (!!!). I get the exact same error if I fail to manually mount the encrypted filesystem before I attempt to login.

So -- what I have to do, until I get it all reconfigured, is wait until the OS tells me that it couldn't successfully mount all the entries in the fstab file. I see that when I get to the login screen. I have the option of S skipping or M manually recovering. If I select S for skip, I get the error (you too?). If I select M I get dropped to a root shell where I can:

#> cryptsetup luksOpen /dev/sdaX /dev/mapper/cryptohome

I'm asked for the password. After entering I mount the encrypted filesystem:

#> mount /dev/mapper/cryptohome /home

Control-D exits the 'recovery shell' and I get back to the login screen which now will work, since /home is actually there.

For this to work automatically, or for a proper password entry request (if it's working in Lucid -- it was VERY flakey in 9.10), you need entries in both /etc/crypttab and /etc/fstab.

I'm typing this in Firefox after logging in and mounting doing just as I described above.

HTH!

---

