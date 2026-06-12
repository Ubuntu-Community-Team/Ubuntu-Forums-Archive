---
title: "Breaking linux security - need help fast"
date: 2011-09-25
forum: General Help
---

### Post by J V on 2011-09-25
Ok, so I lay down for a nap and when I woke up my password was gone. As in erased from my memory.

Everything on my drive is encrypted with ecryptfs or the crucial components are in said home folder and the rest is symlinked elsewhere.

Now I know of a security hole in ecryptfs that allows an ordinary user to see the raw mount data (Just type in mount)

However, there are no other users on my system that I can access.

Everything from email to bookmarks to passwords are stored in the encrypted partition.

In short: I need a way to get in on *any* user account so I can run mount and get the encryption data, then hopefully recover my stuff, but if I reboot the mount will be closed and the only way I'll get it back is to remember the password. Which I can't remember.

To be honest I probably forgot it ages ago and used muscle memory. I know 15 of the 17 alpha-numeric-symbol case sensitive characters, but I only know the order of small sections. Brute forcing from here isn't an option as I set rounds to something like 65000 in /etc/psswd

So yeah, my pretty awesome security is screwing my in the *** right now, anyone know how to fix this? :eek:

---

### Post by haqking on 2011-09-25
> **J V said:**
> Ok, so I lay down for a nap and when I woke up my password was gone. As in erased from my memory.

Everything on my drive is encrypted with ecryptfs or the crucial components are in said home folder and the rest is symlinked elsewhere.

Now I know of a security hole in ecryptfs that allows an ordinary user to see the raw mount data (Just type in mount)

However, there are no other users on my system that I can access.

Everything from email to bookmarks to passwords are stored in the encrypted partition.

In short: I need a way to get in on *any* user account so I can run mount and get the encryption data, then hopefully recover my stuff, but if I reboot the mount will be closed and the only way I'll get it back is to remember the password. Which I can't remember.

To be honest I probably forgot it ages ago and used muscle memory. I know 15 of the 17 alpha-numeric-symbol case sensitive characters, but I only know the order of small sections. Brute forcing from here isn't an option as I set rounds to something like 65000 in /etc/psswd

So yeah, my pretty awesome security is screwing my in the *** right now, anyone know how to fix this? :eek:

if it is your system and physical access then reset your password
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by J V on 2011-09-25
Read the op: encryption...

---

### Post by dave01945 on 2011-09-25
resetting the password won't reset the keyring password and the encrypted home will not be decrypted this would defeat the whole point of encryption

this is why you should make a note of the 32 character unlock code

---

### Post by J V on 2011-09-25
That also defeats the whole point of encryption, if you told someone to write down their password you'd be ridiculed as a windows user.

---

### Post by Paddy Landau on 2011-09-25
Unfortunately, JV, your data is encrypted.

Short of hiring a supercomputer, you need either your password or your 32-character unlock key.

Sorry.

EDIT: In future, please do store your 32-character unlock key. You can store it in a safe or some other secure location if required.

---

### Post by dave01945 on 2011-09-25
> **J V said:**
> That also defeats the whole point of encryption, if you told someone to write down their password you'd be ridiculed as a windows user.

depends if you ever want to recover your home folder if your root file system gets corrupted or anything like that, you loose everything 

you obviously don't keep it with the computer that would be silly but what is the point of having a recovery code for encryption if you don't have it when you need it

---

### Post by J V on 2011-09-25
Ok new plan, I know two 2 character segments of the password, a 3 character segment, and a 4 character segment, plus a 4 character segment with incorrect case, as the 2 character segment I have no idea of.

I think I could brute force this overnight from a live disc but I'd need to write a program for it manually, does anyone know what type of library I could use for this and how to go about it?

---

### Post by haqking on 2011-09-25
> **J V said:**
> Read the op: encryption...

ahh yeah my bad sorry didnt read, just read the forgot password part, so used to seeing that on here.

mm yeah well at least you know its secure.

brute force based on what you know is likely to be the only option, and use better password/passphrase mechanisms next time so you dont forget it.

good luck

---

### Post by dave01945 on 2011-09-25
> **J V said:**
> Ok new plan, I know two 2 character segments of the password, a 3 character segment, and a 4 character segment, plus a 4 character segment with incorrect case, as the 2 character segment I have no idea of.

I think I could brute force this overnight from a live disc but I'd need to write a program for it manually, does anyone know what type of library I could use for this and how to go about it?

personally i think this will take a very long time you may know the majority of the password but the password hash is generated with a randomly generated salt you will have to try every password combination with every salt combination although you could get lucky and find it early but it is very un-likely

--EDIT--
forgot the salt is included in the shadow file anyway

---

### Post by J V on 2011-09-25
Image/zip concatenation and messing with some metadata is likely to be the best option for storing something like that sadly.

I need to know a library (Any language will do, I've used almost anything) that can hash with salt and do it many times (65k something rounds)

For one thing looping a hash algorithm 65k times is bound to be slower than an algorithm that does it automatically, for another I have no idea what pam does with the salt, does it prepend it? Append it? Feed it as a secondary variable that's built into the algorithm?

Iirc it's stored as sha512

---

### Post by dave01945 on 2011-09-25
i think john the ripper can do what you want you may need to patch it to deal with SHA512 not sure if it's been implemented yet.

you will obviously have to provide it with your own wordlist haven't used it in a while but *crunch* may be able to help you with that

---

### Post by Dangertux on 2011-09-25
In my opinion if it's hashed as SHA 512 you're going to be at it for a very long time, even if you reduce the entropy of the string considerably. 

If your full  disk is encrypted as opposed to only your home folder (which you said originally that it was but I'm a little confused on that). You are really out of luck due to the fact you won't have access to an unencrypted shadow file.

Honestly, you really should keep the string ecryptfs gives you. 

You can try john the ripper, rainbow crack (you will need a LARGE amount of pregenerated rainbow tables) , ophcrack or hashcat. That is ONLY if you can get the unencrypted shadow file in the first place. 


You're probably better starting over from scratch.

---

### Post by Paddy Landau on 2011-09-25
> **J V said:**
> Ok, so I lay down for a nap and when I woke up my password was gone. As in erased from my memory.
Did you previously remember the password for a long time? You could try a hypnotist. It doesn't work for everyone, but it just may work for you.

---

### Post by Paddy Landau on 2011-09-25
> **J V said:**
> Now I know of a security hole in ecryptfs that allows an ordinary user to see the raw mount data (Just type in mount)Are you sure? I'd love a link to that -- if that hole really exists, it is a serious bug!

> **J V said:**
>  However, there are no other users on my system that I can access.
Well, hang on. Boot into recovery mode and create a new user with admin rights (and remember the password!). Then reboot into your new user.

---

### Post by patryk77 on 2011-09-25
Your best bet would be to copy the shadow file and generate a wordlist with what you remember for John the Ripper, as Dave said.

[img]http://imgs.xkcd.com/comics/password_strength.png[/img]

---

### Post by J V on 2011-09-25
> **Paddy Landau said:**
> Are you sure? I'd love a link to that -- if that hole really exists, it is a serious bug!Any user that can run mount can see the raw decryption passcodes but the partition had to be previously mounted, which is a problem since I can't log in.

Hypnosis is all well and good but I'd rather not have someone poking around in my head.

I didn't know john the ripper handled multiple passes, I'll take a look at that.

It is my home folder that's encrypted, not the entire disk, I can get access to the shadow file but then I have to drop the mount and lose that avenue of pursuit.

When using a wordlist with john, how do I add wildcards, I think I know where the last 2 characters that I'm missing are, and unless it can mix and match words from the wordlist my knowledge (Or assumption) of the password is moot.

how can I tell it to crack all passwords of type: "blablabla**blabla" where it only bruteforces the **

Edit: Is it possible to do a hot boot with only software to rip the encryption code from memory or would I need liquid nitrogen -_-

---

### Post by dave01945 on 2011-09-25
if you look at the documentation for **crunch** you can generate a list for what you need you can either save the list to a text file to use with john or you can pipe it straight into john then there is no need to create a big file

you can get crunch here

[crunch](http://sourceforge.net/projects/crunch-wordlist/)

it is not in the ubuntu repositories

there is a online manpage here if you want to have a look first you just need to set a pattern for the wordlist randomising what you don't know it can do what you need

[Crunch Manpage](http://www.irongeek.com/i.php?page=backtrack-r1-man-pages/crunch)

---

### Post by Dangertux on 2011-09-25
> **J V said:**
> Any user that can run mount can see the raw decryption passcodes but the partition had to be previously mounted, which is a problem since I can't log in.

Hypnosis is all well and good but I'd rather not have someone poking around in my head.

I didn't know john the ripper handled multiple passes, I'll take a look at that.

It is my home folder that's encrypted, not the entire disk, I can get access to the shadow file but then I have to drop the mount and lose that avenue of pursuit.

When using a wordlist with john, how do I add wildcards, I think I know where the last 2 characters that I'm missing are, and unless it can mix and match words from the wordlist my knowledge (Or assumption) of the password is moot.

how can I tell it to crack all passwords of type: "blablabla**blabla" where it only bruteforces the **

Edit: Is it possible to do a hot boot with only software to rip the encryption code from memory or would I need liquid nitrogen -_-

You should find this useful when configuring JTR 
[http://higherintellect.info/texts/computing/general/john.txt](http://higherintellect.info/texts/computing/general/john.txt)

---

### Post by J V on 2011-09-25
Wordlist rules lead me to think I need something like:
```
blablabla?z?zblablabla
```as a wordfile, anyone with experience can confirm?

Edit: Nope I'm doing it wrong. Expecting something like regex but don't know how. Not gonna turn off machine and lose an avenue until I know I can do this right

---

### Post by Dangertux on 2011-09-25
> **J V said:**
> Wordlist rules lead me to think I need something like:
```
blablabla?z?zblablabla
```as a wordfile, anyone with experience can confirm?

The ?z?z is matching two characters of any type. Is that what you want?

---

### Post by J V on 2011-09-25
Yes but would a file with just those contents work?

---

### Post by dave01945 on 2011-09-25
i think the command you want if the missing two characters are alpha numeric would be 

```
./crunch 8 8 -f charset.txt mixalpha-numeric -t bla@@bla -o wordlist.txt
```

charset.txt is the one that came with crunch it will be in the same directory the numbers 8 8 i have used as an example you will want to change that to be the same as your pass length and the @ symbols will be all that is replaced the bla bla will stay the same

also you don't have to save it to file it can be piped directly to john just tell john to take input from stdin (--stdin) 

also about the mount option with another user all that shows is the key signature that can't be used for decryption but if you could login as root or another admin user you could have access to the files that are already mounted but as you said you have no other users so don't think that is possible

---

### Post by Dangertux on 2011-09-25
I'm confused are you generating a wordlist for JTR with crunch or are you doing it manually? the above blablah?z?zbla example would be for a JTR word list where JTR would enumerate the possibilities itself.

Crunch is a whole different hat, so which are you using?

---

### Post by J V on 2011-09-25
I wasn't using crunch, would this file just work with jtr?

I'd rather avoid piping a huge crunch command to john

Edit: Have the psswd and shadow files, mix n matched to get this:
```
j:$6$rounds=65537$lp8ss8/8$UKXMnnninPnGsPZGY04rhkRq6cMrJKhyaCRUDFENIhFxm/4COz.ZDayhnO1PUTVUgHsWn7eR.cJ7AV2CvCJPn0:1000:1000:Hello ubuntu forums,,,:/home/j:/bin/bash
```jtr isn't accepting it, what's wrong with it?

---

### Post by J V on 2011-09-26
Bump! Help! I slept on it and still can't remember password!

My only hope now is that I can brute force it, but if john won't load the hash we have a different problem. Does jtr even support rounds?

---

### Post by dave01945 on 2011-09-26
what version of john are you using because support for SHA512 wasn't added until 1.7.6 and the version in the ubuntu repo's is 1.7.3

also i don't think john supports the format you have given it from above did you use john's unshadow script to extract the hash also this video may be of use to you

[http://www.youtube.com/watch?v=kxWo7-pk6DY](http://www.youtube.com/watch?v=kxWo7-pk6DY)

---

### Post by J V on 2011-09-27
No I didn't. Oh never mind, I reinstalled a system from scratch. Aside from losing all my stuff, keyring, firefox passwords/bookmarks this new system is doing much better anyway.

---

### Post by haqking on 2011-09-27
> **J V said:**
> No I didn't. Oh never mind, I reinstalled a system from scratch. Aside from losing all my stuff, keyring, firefox passwords/bookmarks this new system is doing much better anyway.

well thats why backups exist.

have a backup of everything, saves headaches in the future ;-)

---

