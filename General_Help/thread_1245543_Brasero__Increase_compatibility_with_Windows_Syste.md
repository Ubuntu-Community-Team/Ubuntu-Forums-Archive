---
title: "Brasero:  Increase compatibility with Windows System"
date: 2009-08-20
forum: General Help
---

### Post by UranUtan on 2009-08-20
Hi,

Using Ubuntu 9.04 x64, Brasero 2.26.1

Sometimes when folders and file names are a little bit long such as:

My Music Collection Backup (July 2009)\01 - My Favorite Artist - He's kicking, screaming and snooring.mp3

When I click "Burn" (the project type is data, not audio), the "Increase compatibility with Windows System" is automatically unchecked. If I force the box to be checked then tthere is a warning message that says file name longer than 64 chars will be truncated.

[COLOR="Red"]Question:[/COLOR] what is this 64 chars limit? Windows is capable of writing long file name in CD/DVD. If I transfer the files on an external drive and use Windows system to burn the DVD (using a freeware CD burner). The compilation is burnt OK without any complaint and all long file names are intact. Why would Brasero incorrectly assume that Windows cannot handle these long file names?

---

### Post by matthewbpt on 2009-08-20
I think it may be older windows versions that aren't compatible. What version do you have?

---

### Post by UranUtan on 2009-08-20
> **matthewbpt said:**
> I think it may be older windows versions that aren't compatible. What version do you have?

I use Windows XP SP3 and Windows 2008 Server x64 both are up to date.

We are in 2009, Brasero must be reasonable enough to compare with a decent Windows version. Otherwise, Windows software can even argue that Linux doesn't know how to use a mouse or USB drive or anything silly like that.

---

### Post by ghostborg on 2009-08-20
Brasero just makes coasters for me. K3b and Nero linux work fine,every burning app but Brasero works. Strange. I even did a fresh install with 9.04.
I try it every so often when an update comes out but same result- coaster.
Jaunty 9.04 AMD64 pioneer drive.

---

### Post by matthewbpt on 2009-08-20
Well the option of remaining compatible should still be there in case the user wants it, though I admit it would be helpful to say what version of windows it is talking about. The program isn't arguing anything, it is just giving the option to conform to the character limit, which is part of the original ISO9660 specification for CD file systems.

---

### Post by pastalavista on 2009-08-20
The Brassero warning should probably be updated to specify compatibility issues with "older" Windows systems. But you can leave the box unchecked and it will be perfectly compatible with a modern system. This is a handy feature if you happen to be using older Windows systems too. Doesn't Windows also warn you about backward compatibility issues?

---

### Post by UranUtan on 2009-08-20
> **pastalavista said:**
> The Brassero warning should probably be updated to specify compatibility issues with "older" Windows systems. But you can leave the box unchecked and it will be perfectly compatible with a modern system. This is a handy feature if you happen to be using older Windows systems too. Doesn't Windows also warn you about backward compatibility issues?

I just went ahead and burn a data DVD with the "Increase compatibility with Windows System" UNCHECKED. Then read that DVD on a Windows XP machine. ALL folder & file names are truncated.

My Music Collection Backup (July 2009)\01 - My Favorite Artist - He's kicking, screaming and snooring.mp3

becomes

MYMUS_01\01MYF_01.MP3

Strangely enough, when this DVD is read using Ubuntu, Nautilus can display all the original long file names. That prompts a 2nd question: what had Brasero put in the DVD do that Ubuntu sees long filename and Windows sees short file name?

And also what does Ubuntu do to see long file names written into a data DVD by a Windows program? I think I am going to file a bug in Launchpad. That is strange that nobody notice this bug yet.

---

### Post by UranUtan on 2009-09-12
Hi,

Problem solved. Not by Brasero but I have installed K3B which fulfills perfectly my needs. K3B has excellent GUI and doesn't have all the Brasero bugs (strange sort order, no space used indicator, and weird long file name handling).

The most surprising is that a KDE program can also work in GNOME desktop. I hope there will be no side-effects.

---

### Post by The Cog on 2009-09-12
k3b is my favourite too. It always seemd to get it right when other burning programs go badly wrong.

There's no problem using KDE apps in Gnome except that the desktop integration isn't that great - the fonts don't look the same as other apps for instance.

---

