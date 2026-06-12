---
title: "Can't type acute accents anymore"
date: 2009-09-27
forum: General Help
---

### Post by rannuG on 2009-09-27
I recently posted a thread similar to this one in Absolute Beginner Talk as I thought this wasn't too hard to solve. I might have been wrong.

The problem is that I can't type acute accents anymore. I'm from Iceland and thus this is a major problem for me. I used to be able to press two keys: the English apostrophe button and a vowel. 
However, when experimenting in Keyboard Preferences, pressing Reset to Defaults disabled that option. I've tried numerous things in Layout Options to fix it but nothing seems to work.

I'm a Ubuntu 9.04 user and using a Logitech Cordless Desktop EX110 keyboard.

I'll post my Keyboard settings here: [http://i568.photobucket.com/albums/ss121/Dendrophilia/keyboard.jpg](http://i568.photobucket.com/albums/ss121/Dendrophilia/keyboard.jpg)

In Layout Options, the only things I've selected are 'Keys to change layout' (both shift keys  together) and 'Key to choose 3rd level' (right ctrl).

Are there any ideas to fix this? Or maybe I'll just have to wait for Ubuntu 9.10?

Thanks in advance.

Added: I've tried compose keys too without luck. The icelandic keyboard has dead keys but they don't work for me anymore.

---

### Post by CatKiller on 2009-09-27
> **rannuG said:**
> I used to be able to press two keys: the English apostrophe button and a vowel.

That sounds like you were using "dead keys" before. If you want it to behave like that you'll need to pick a layout that uses dead keys.

The other option is to set a Compose key. Then you can press Compose &#8594; accent &#8594; letter. For example, Compose &#8594; ' &#8594; a gives you á. It's slightly more flexible than dead keys in that you can generate non-letter characters too; Compose &#8594; o &#8594; c gives you the copyright symbol ©, and so on.

---

### Post by rannuG on 2009-09-27
The Icelandic default keyboard supports acute accents.
I tried compose keys, but didn't work.

This is really strange...

---

### Post by rannuG on 2009-09-27
Maybe it might help mentioning that an Icelandic friend of mine uses Ubuntu 9.04 too and has the same keyboard options as me, except he has nothing selected in layout options (I tried deselecting mine but didn't work).

---

### Post by rannuG on 2009-09-27
Any ideas?

---

### Post by rannuG on 2009-09-28
Can anybody help me on this?

---

### Post by StuartN on 2009-09-28
> **rannuG said:**
> Can anybody help me on this?

You should try the same version of the Iceland keyboard as the one that worked - try print preview of the various Iceland layouts to find where the dead keys are.

The compose key works by selecting, for example, the right-control key as compose and then pressing compose, accent, character instead of accent, character with dead keys.

In another thread someone said options work for new users (i.e. create another user account) that simply do not function on the primary account.

---

### Post by rannuG on 2009-09-29
I created a new account and that solved the problem. Thanks! 

Pretty annoying to move all the files though and grant permissions, but I've wanted to change a username for a while anyway...

---

### Post by StuartN on 2009-09-29
> **rannuG said:**
> I created a new account and that solved the problem.

I wish I knew what setting is buried somewhere in the installation-time administration user that disables keyboard functionality. No matter what settings I can think of, they have all been correct.

---

### Post by ErikJanVens on 2009-11-04
Same here. New user and diacritics work again. I select Icelandic keyboard and I do not need a Compose-key. Just press diacritic and vowel.

---

### Post by Smari on 2010-09-28
Hi I have exactly the same problem. I am Icelandic and I can't write acute accent to my letters. I am running Ubuntu 10.04.:guitar:
 This was working well until I changed the keyboard layout to Finnish for a while. When I changed it back to Icelandic the acute accent button did not work any more. I wish there was a way of fixing this with out having to make a new account...:confused:

---

### Post by white_phantom on 2011-09-28
I had a similar problem and just want to briefly comment how I fixed it in case someone else runs across this thread with a similar problema. 

Problem: after an upgrade the tilde stopped appearing on top of the next letter but rather before it, so instead of  á I was getting 'a.

I fixed it by erasing some keyboard layout definitions at the end of my .profile file in my home directory. 

Hope this might help someone.

---

