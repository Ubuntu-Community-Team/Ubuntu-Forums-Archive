---
title: "GDM Could Not Write To Your Authorization"
date: 2006-05-13
forum: General Help
---

### Post by Jack Jebedee on 2006-05-13
I was away for a while so, when I fired up Ubuntu this morning, I got 73 updates.  GREAT!  I had Ubuntu shut off the computer afterward, then I came back this evening to login.  This is what I saw:

[COLOR="Sienna"]GDM could not write to your authorization file.  This could mean that you are out of disk space or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator.[/COLOR]

I am my system administrator.  Bummer.

The hard drive has more than 7Gb free space.  Don't know why my home directory can't be opened.

Is this Ubuntu's way of telling me that I'm screwed?  I would appreciate any alternatives to wiping Breezy off my drive and starting over.

... JJ

---

### Post by Ramses de Norre on 2006-05-13
log in recovery mode and do chown -R username /home/username && chmod -R 664 /home/username
Check whether your sure you've got space left in your home directory.

---

### Post by Jack Jebedee on 2006-05-13
Great idea!  Except that I can't find "recovery mode" in the Wiki.  How do I log in recovery mode?  I know there must be fairly detailed instructions in the Ubuntu archives, but I can't find them.  A pointer in the right direction would help a lot.

By the way, the opening screen (where I enter my username and password) already has my username// on the lower right corner of the screen, next to the date.  I don't remember that being there before.

Thanks very much for the help!

... JJ

---

### Post by sinkxdie on 2006-05-13
Do you use Grub? Because if you do it should be right under your existing kernels.

---

### Post by Jack Jebedee on 2006-05-13
It might be, but I can't find any kernels.  All I have is a screen that requires me to enter an account name and a password.  That's it!  Oh, and there's still [COLOR="DarkRed"]username//[/COLOR] on the bottom-right corner of the screen, though I don't know how it knows who I am *_before_* I login.

Thanks very much for your suggestion.  Even though I have no clue what to do with it (if I can do *_anything_* to resurrect Breezy), I appreciate your reply.

... JJ

---

### Post by tarkus on 2006-05-13
The option to boot into Recovery mode is available at the GRUB prompt, which is before Linux even begins to load.  It is immediately after the BIOS finishes doing its stuff.  You will see a line along the lines of "Verifying DMI Pool Data..."  (at least on all of my computers) followed by an "Press ESC to list kernels..." or some such line.  Press the escape key there and it should give you a Recovery mode option.

---

### Post by Jack Jebedee on 2006-05-14
[COLOR="Red"]Aha![/COLOR]  I'll try it as soon as I get home.  Thanks, Tarkus!  You're beautiful.  And thanks all for answering.  I'm starting to get good feelings about this.

... JJ

---

### Post by Jack Jebedee on 2006-05-15
I followed Ramses de Norre's instructions:  [COLOR="Blue"]log in recovery mode and do chown -R username /home/username && chmod -R 664 /home/username  Check whether your sure you've got space left in your home directory.[/COLOR] as best I could.  The double ampersand didn't seem to work, though, so I entered the commands separately at the command prompt:
[LIST=1]
[*]chown -R username /home/username
[*]chmod -R 664 /home/username
[/LIST]
Interesting!  The computer thought about each command for a second or two, then returned to the command prompt.  There was no indication of space left anywhere -- not on the hard drive, not in the directory -- and all I saw was a command prompt in front of me.  However, I did manage to change to the [COLOR="DarkGreen"]Desktop[/COLOR] directory and, just because it couldn't hurt, I deleted a few large files I kept there, hoping that it would make more room on the drive (just in case a full drive was the problem).  Then I rebooted.  I entered my username and password at the opening screen and this was the greeting I got from the Badger:

[INDENT][COLOR="Sienna"]Your $home/.dmrc file has incorrect permissions and is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.[/COLOR][/INDENT]

Oh?  I think I know the translation for THAT message:  "You're screwed, Jack.  Give up.  Go away.  Come back when you're ready to re-install the OS."  I think my Breezy Badger just committed suicide by upgrade.  (I have no proof, but just a suspicion, that the automatic upgrade *might* have been successful had the Badger taken smaller bites instead of trying to install 73 upgrade files at once.)

I tapped the space bar and saw that the Badger had one more greeting:

[INDENT][COLOR="Sienna"]GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator.[/COLOR][/INDENT]

Hey, I've already seen that one.  It's what I was trying to fix!  I guess it didn't get fixed.

Never mind.  I swapped my boot drive for the one that holds my ancient Windows ME.  It's not Ubuntu, but it works.

I won't re-install Breezy Badger.  I'll work with Windows ME for [COLOR="DarkRed"]18 days [/COLOR]and [COLOR="Red"]THEN[/COLOR] I'll install a fresh, new copy of [COLOR="DarkOrchid"]Dapper Drake[/COLOR]!  Drakes live longer than Badgers, don't they?  I'll be sure to make it a dual-boot setup with Windows ME, just in case they don't.

Thanks very much for the help.  Even though we couldn't resurrect the Badger, it was terrific getting suggestions so that I didn't feel so helpless *and* alone.  I'm glad you're here.

... JJ

---

