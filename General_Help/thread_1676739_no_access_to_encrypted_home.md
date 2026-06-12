---
title: "no access to encrypted home"
date: 2011-01-27
forum: General Help
---

### Post by wotan684 on 2011-01-27
Hi, I have choosen to encrypt Ubuntu 10.10 during installation (no alternate installation).
After some time of working properly I get following error message after I put in correct password :

"Could not update ICE authority file /home/surf1/.ICE authority"

When I click "ok" following error message is shown :

"there is a problem with the configurationserver (/usr/lib/libconf2-4/gconf-sanity-check-2 finished with status 256)"

When I click this "ok" next error message appears :

"Nautilus could not create following necessary files : home/surf1/Desktop,/home/surf1/.nautilus"

After I click here ok nothing else happen anymore and I get not access to my account and so to my data.

How can I solve this problem ?

Thanks very much for your support in advance

Cheers wotan684

---

### Post by donnie309 on 2011-02-03
hi I saw this problem on a different forum when looking up info on /home encryption. Hope this helps.

ejoey wrote on 2009-11-14: 	#2

Hi,

I've got the same problem. I've changed my user password with the passwd command. I have an encrypted home folder and got the same error message when I tried to log in. The only solution i found was to get back to my old password.

Please, let me know if you found a better way to fix it without keeping the old password.

Thanks

---

### Post by albinootje on 2011-02-03
> **wotan684 said:**
> 
After some time of working properly I get following error message after I put in correct password :

"Could not update ICE authority file /home/surf1/.ICE authority"

Your partition which has your /home directory might be full. Boot into recovery mode (or with a Linux "live" cdrom or usb-stick) and see whether that is the case, and if so, clean up some files, for example in /var/cache/apt/archives/

---

### Post by 86themachine on 2011-07-23
If your home folder is Encrypted, Decrypt your home folder prior to attempting a fix of the ICEauthority. (Credit for this goes to others Im just combining the parts I found to make it simple as I had the same problem). There seems to be several options to fixing the "Could not update ICEauthority file" you can search for other solutions but none that I know of will work until you decrypt the home folder.

1)
Code: 

sudo ecryptfs-unwrap-passphrase /home/user/.ecryptfs/wrapped-passphrase

Enter your account password for the user account, this will then display the encryption key, take a note of this key, if the user account password is wrong you won't be able to retrieve the key.

2)
Code:

sudo ecryptfs-add-passphrase --fnek

Enter the key you retrieved in step 1. This will insert two auth tok with sig. Take a note of the second key.

3)
Code:

sudo mount -t ecryptfs /home/user/.Private /home/user/Private


    * Enter your key (Noted in step one)
    * Select: aes (use the aes cipher)
    * Select: 16 (use a 16 byte key)
    * Enable plaintext passthrough: n
    * Enable filename encryption: y )
    * Filename Encryption Key (FNEK) Signature: (Enter the key noted in step 2)
    * Since you are using superuser privileges instead of your regular user account, you may get a warning that you might have entered the passphrase wrong, even if you didn't. Continue the mount operation and don't save the key if it asks.

Assuming you entered your key correctly, you should be able to temporarily access your data at /home/user/Private

Now Attempt To Fix "ICEauthority"
Another suggestion was to make sure that the entire home directory belonged to the user (me).  That sounded like it might be on the money.  My impression was that moving around and copying this old /home partition could easily have screwed up the permissions.  So now, how to make sure I owned the whole /home directory?  In Nautilus (i.e., Places > Computer), I right-clicked on Home Folder > Properties > Permissions.  It said root (i.e., not ray) was the owner.  In Terminal, I typed "sudo nautilus" and, using the Tree (i.e., not Places) view (top of left panel), went to File System > home > ray > right-click Properties > Permissions and changed the permissions to me with full access.  I clicked on the "Apply Permissions to Enclosed Files" button, closed out of there, and rebooted.  Eureka!  That was the solution.  Done!

---

