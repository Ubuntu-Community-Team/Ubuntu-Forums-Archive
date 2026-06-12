---
title: "obnoxious keyring, password three times, blah blah blah"
date: 2011-07-28
forum: General Help
---

### Post by BuddyThirteen on 2011-07-28
So like a lot of people seem to have done, I tried to make it so I don't have to enter my password (Why is this so hard? I don't want to have to enter my password!). I marked "Do not ask on login" -- okay, great. Right? No. Like those same people, I found out that in exchange for the "convenience" of not having to enter my password once, I now have to enter it three times. Stupid stupid stupid. No, that's not my password, that's my sentiment. Anyway.

I read the solutions, turns out you need to enter your password like a chump if you don't want that dumb keyring popping up. So I went to "Users and Groups" and clicked the "Change" button. The little box for requiring on login is already unchecked. Whatever. So I tried maybe changing my password, and checking and unchecking the box, just to see if the changes took.

Sidenote, hilariously, if you change your password to add a "1" to the end just for the sake of changing it, Ubuntu has no problems. But if you then try to change it back to remove the "1" -- turns out that's too similar to your last password, and you can't change it back. So you need a third throwaway password to use between them. How dumb is that?

Anyway, point is: Every time I start up now, it still logs me in automatically (convenient!) and then asks me for my password three times (retarded!). How the hell do I fix this? I'm fine entering my password on login if that's what it takes to avoid this big pile of stupid, but it doesn't seem to want to work. Alas.

It's Natty, if you needs to know. Let me know if you need any other info.

---

### Post by pqwoerituytrueiwoq on 2011-07-28
if you set the password as null (blank/empty) it will shut up, but anyone with access to the system can get your passwords (empathy/mail-notification/evolution mail/wifi)

---

### Post by BuddyThirteen on 2011-07-28
> **pqwoerituytrueiwoq said:**
> if you set the password as null (blank/empty) it will shut up, but anyone with access to the system can get your passwords (empathy/mail-notification/evolution mail/wifi)
I think I tried that once and it said I couldn't do it. But I'll try again. Also, I know that the user password and the keyring password are only the same when you set them at initial setup, and if I do make the user password blank, how do I also blank the keyring password?

---

### Post by mcduck on 2011-07-29
> **BuddyThirteen said:**
> I think I tried that once and it said I couldn't do it. But I'll try again. Also, I know that the user password and the keyring password are only the same when you set them at initial setup, and if I do make the user password blank, how do I also blank the keyring password?

Don't set your login password blank, that won't help you at all. (besides that would be *really* unsafe thing to do if you are using an admin account!)

Just set the _keyring password_ as blank instead. That makes the Gnome Keyring store things in unencrypted format, avoiding the need to unlock the keyring when programs try to access data from it. it's less safe than keepin g the keys encrypted when you are not logged in, but since you want to use automatic login such things probably aren't a lot opf concern to you anyway. ;)

You can use the "PAsswords and Encryption Keys"-tool found in the System Settings to change your keyring password. just right-clcik on the default keyring, select "Change Password", type in the current password  and set the fields for new one empty.

---

### Post by Mr.Kappa on 2011-07-29
Try the PAM usb module. When in need of unlocking your keyring just pop in your usb stick. That's much more safer than leaving the passwords unencrypted!!

---

### Post by lailokenwiz on 2011-07-29
mcduck's solution works fine thanks.
I have a security question. (a bit newby)
I have no security issues locally (home) but ...
If I auto login and have keyring blank am I more open to attack from outside as well?
Is it easier to go into my system from outside this way (considering "they" don't know my password?

---

### Post by BuddyThirteen on 2011-07-29
Thank you for the responses, it's working great now. I left the login password alive (so I still need it for system changes and software installs, which is perfect) and the keyring blank. It's not a super security risk for me, because nobody but me has physical access to this computer, which is why I found the password situation inconvenient.

For my publicly accessible computer, I just encrypt the whole OS with TrueCrypt.

---

### Post by haqking on 2011-07-29
blank passwords and circumvention of the security model will just bring you back to the forum with support issues relating to the fact that elevated privelege is their all the time beause it doesnt require authentication.

Security is a process not a product or setting, continual vigilence and awareness is needed all the time to prevent possible attacks, malware and basic everyday task going a wry from not using least privelege.

Best to learn to love the security and requirement to enter credentials for authentication rather than have to learn to recover from a trashed system ;-)

---

### Post by haqking on 2011-07-29
> **BuddyThirteen said:**
> Thank you for the responses, it's working great now. I left the login password alive (so I still need it for system changes and software installs, which is perfect) and the keyring blank. It's not a super security risk for me, because nobody but me has physical access to this computer, which is why I found the password situation inconvenient.

For my publicly accessible computer, I just encrypt the whole OS with TrueCrypt.


it is not just about physcial access remember, it is also about processes and remote execution.

But at least you havent made your account password blank so dont get lulled into that aswell

---

### Post by Mr.Kappa on 2011-08-03
> **lailokenwiz said:**
> mcduck's solution works fine thanks.
I have a security question. (a bit newby)
I have no security issues locally (home) but ...
If I auto login and have keyring blank am I more open to attack from outside as well?
Is it easier to go into my system from outside this way (considering "they" don't know my password?
Just like haqking said.. removing your password leaves your system/keyring/anything else pretty much vulnerable.
Like I said use the pam usb modules or something similar but DON'T leave your password "blank"

---

### Post by BuddyThirteen on 2011-08-03
> **Mr.Kappa said:**
> Just like haqking said.. removing your password leaves your system/keyring/anything else pretty much vulnerable.
Like I said use the pam usb modules or something similar but DON'T leave your password "blank"
I left the user password intact, but I blanked the keyring. The keyring is a nuisance and I feel that the user password is sufficient to protect my system from baddies. I mean, what does the Keyring protect? My Gwibber login? I honestly don't know what else, so let me know if it's the sole layer of protection between an accidental keystroke and the self-destruct button. Then I might put it back up.

---

### Post by haqking on 2011-08-03
> **BuddyThirteen said:**
> I left the user password intact, but I blanked the keyring. The keyring is a nuisance and I feel that the user password is sufficient to protect my system from baddies. I mean, what does the Keyring protect? My Gwibber login? I honestly don't know what else, so let me know if it's the sole layer of protection between an accidental keystroke and the self-destruct button. Then I might put it back up.

your keyring is exactly what it says, it is like your keyring in your pocket with house key, shed key, car key, personal safe key or whatever.

Any keys stored on your system for use for connection to your wireless networks for example.  It is a master key to unlock all your stored keys/passwords so that you only need to enter one.

I mean it is not a major concern if physically you are the only uses your machine for example, it is just bad practice to use blank passwords so best to maintain what security you can to avoid headaches ;-)

---

### Post by BuddyThirteen on 2011-08-03
> **haqking said:**
> I mean it is not a major concern if physically you are the only uses your machine for example, it is just bad practice to use blank passwords so best to maintain what security you can to avoid headaches ;-)
Yep. Only dude on this machine ever. I'm actually pretty thorough when it comes to computer security-- using TrueCrypt for personal files, KeePass to generate awesome passwords (you should see the password for my bank, I used the full 64char limit and activated even non-ASCII characters). I used to use a variant of the same password for everything, but now I like the idea that if anyone cracks one of my passwords, they can't just copy/paste to get access to everything I have.

But anyway...

---

### Post by haqking on 2011-08-03
> **BuddyThirteen said:**
> Yep. Only dude on this machine ever. I'm actually pretty thorough when it comes to computer security-- using TrueCrypt for personal files, KeePass to generate awesome passwords (you should see the password for my bank, I used the full 64char limit and activated even non-ASCII characters). I used to use a variant of the same password for everything, but now I like the idea that if anyone cracks one of my passwords, they can't just copy/paste to get access to everything I have.

But anyway...


thats good.  depending on how you use it the keyring can be like a key to the safe where all your other keys are stored which makes the security of all the locks null and void ;-)

but sounds like not too much of a problem for your particular situation.  I just never recommened a blank password for anything, though i tell people they can fix this keyring issue by supplying one i still never condone it.

For me i use complicated passwords for everywhere i can use one.

---

### Post by mcduck on 2011-08-04
> **BuddyThirteen said:**
> I left the user password intact, but I blanked the keyring. The keyring is a nuisance and I feel that the user password is sufficient to protect my system from baddies. I mean, what does the Keyring protect? My Gwibber login? I honestly don't know what else, so let me know if it's the sole layer of protection between an accidental keystroke and the self-destruct button. Then I might put it back up.

The keyring keeps the information stored in it encrypted when the keyring is locked. This means that even if somebody gets physical access to your computer they can't get your passwords and other keys. (physical access counts as root access, compromising all files on the system that aren't encrypted)

Also, *you* might only have Gwibber password there, while other people can actually have some PGP encryption keys, important server passwords and whatever things that really shouldn't get in the hands of other people. Not even in the worst case of a stolen computer.

So how necessary the keyring password is simply depends on how important data you store there. :)

(what comes to the user password being enough to protect you, that's exactly how it works. If you use a password login that will unlock the keyring for you, so you normally don't need to do anything extra to get the security the keyring can give you.)

---

