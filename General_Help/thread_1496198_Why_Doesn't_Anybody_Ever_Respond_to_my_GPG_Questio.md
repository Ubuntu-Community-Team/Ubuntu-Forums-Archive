---
title: "Why Doesn't Anybody Ever Respond to my GPG Questions?"
date: 2010-05-29
forum: General Help
---

### Post by clevertomato on 2010-05-29
I've posted same question different times over the months and never get any responses. I also have tried many different times on IRC #ubuntu with the same results--SILENCE. What gives? Does nobody use GnuPG anymore?

I can't get it to prompt me for secret key when I need to use it. I don't want to put my secret key(s) on my hdd for what should be obvious reasons. If it's not on my hdd, GnuPG / Seahorse just thinks I don't have the key.

---

### Post by smcleish on 2010-05-29
I've not actually seen your earlier posts, but I'm willing to have a go at helping you out. I use gpg, though I wouldn't call myself an expert.

There's not enough here to work out what the problem is, but I can guess that one issue could be that the software is looking for the key in a particular location, probably $HOME/.gnupg (going by the manual at [http://www.gnupg.org/gph/en/manual.html](http://www.gnupg.org/gph/en/manual.html)). I store quite a lot of stuff off my hard drive, so I can easily swap it between machines, and the way I generally do this is as follows.

Let's assume that the normal location for configuration files for a particular application is a hidden directory in the user's home directory, as is the case for gpg. Create the hidden directory in whatever the usual way is (in the case of gpg, generating the public key). Then mount the device you want to use to store the configuration. Move the hidden directory to the device (this sometimes works better if the directory on the device is not hidden). Then create a symbolic link from the directory on the device to the standard hidden location in your home directory.

So:

```

% gpg --gen-key
% ls -lad .gnupg
[mount device, say as /media/device]
% mv .gnupg /media/device/gnupg
% ls -lad /media/device/gnupg
% ln -s /media/device/gnupg .gnupg
% ls -la .gnupg

```

(the ls commands are to check that the directories have been created).

When you next wish to use gnupg, attach and mount the device. gnupg and other software which uses the .gnupg directory should then work fine. If this does not happen, I would guess that the most likely problem is permissions, but detailed information would be needed to sort it out.

---

### Post by clevertomato on 2010-05-29
> **smcleish said:**
> I've not actually seen your earlier posts, but I'm willing to have a go at helping you out. I use gpg, though I wouldn't call myself an expert.

There's not enough here to work out what the problem is, but I can guess that one issue could be that the software is looking for the key in a particular location, probably $HOME/.gnupg (going by the manual at [http://www.gnupg.org/gph/en/manual.html](http://www.gnupg.org/gph/en/manual.html)). I store quite a lot of stuff off my hard drive, so I can easily swap it between machines, and the way I generally do this is as follows.

Let's assume that the normal location for configuration files for a particular application is a hidden directory in the user's home directory, as is the case for gpg. Create the hidden directory in whatever the usual way is (in the case of gpg, generating the public key). Then mount the device you want to use to store the configuration. Move the hidden directory to the device (this sometimes works better if the directory on the device is not hidden). Then create a symbolic link from the directory on the device to the standard hidden location in your home directory.

So:

```

% gpg --gen-key
% ls -lad .gnupg
[mount device, say as /media/device]
% mv .gnupg /media/device/gnupg
% ls -lad /media/device/gnupg
% ln -s /media/device/gnupg .gnupg
% ls -la .gnupg

```

(the ls commands are to check that the directories have been created).

When you next wish to use gnupg, attach and mount the device. gnupg and other software which uses the .gnupg directory should then work fine. If this does not happen, I would guess that the most likely problem is permissions, but detailed information would be needed to sort it out.
smcleish: Thanks for responding.

I have avoided learning about and using symbolic links thus far in Linux because they seem a little confusing and intimidating to me. That said, let me describe a little more about what I hope to accomplish with GnuPG and maybe that will confirm whether or not you think your proposed solution is still what you recommend (because I'm not sure I fully understand your suggestion).

I know GnuPG is not identical to PGP, but for clarification... I used to use PGP from about version 5-ish to 8. I was able to set the location of my keyrings in PGPKeys. I pointed it to my hdd for my public keys, but I pointed it to the path of a USB Flash memory device for my secret key(s). When I started to do anything that needed the secret key, I would be prompted for it (since it was not on my hdd), at which time I would plug in my USB device, then click OK. PGP found the secret key, used it, and everything worked fine. If I was done with my secret key for a while, I'd unplug my USB device.

Is there any way for me to get this kind of behavior from GnuPG?

I also wish I GnuPG had something like "encrypt current window" like PGP had, but that's another question for another thread I suppose. This existing thread is more important to me and it's been hard enough to get answers to it.

---

### Post by smcleish on 2010-05-29
OK, that's what I thought you'd want to do. My solution should work.

The symbolic link is a soft link, which means that it should appear to gpg to be the directory it would expect when the USB device is correctly mounted, but would give an error if you try to use gpg when it isn't mounted. That said, some applications are not savvy about symbolic links, so you'd have to try it to see if it works. (This would apply not just to gpg itself, but to things like the enigmail extension to thunderbird which use gpg.)

Alternatively, it is possible to make gpg use a different directory, according to [http://www.gnupg.org/faq.html#q4.18](http://www.gnupg.org/faq.html#q4.18) - I've not tried this, so I can't guarantee it would work with a directory which isn't permanently connected. It also looks as though you could set $GNUPGHOME in your profile to make gnupg use a directory on the USB stick.

Of all the options, I think I'd try $GNUPGHOME first, then using the --homedir option, then the soft link. Your problem in each case is likely to be that applications other than gpg itself may not be clever enough to follow through and pick up what you've set.

Simon

---

### Post by clevertomato on 2010-05-30
Thanks a lot. I will proceed as you suggest and will let you know after I've had an opportunity to see how things go.

---

