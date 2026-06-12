---
title: "text files"
date: 2011-07-19
forum: General Help
---

### Post by Scooter_X on 2011-07-19
So, maybe this is, maybe this isn't the place for this. I just want to learn a bit more about the text files that are created by gedit. 

In Windows, there's always the '.txt' extension. Not so in Linux. What is the reason for that? The thing that sparked this question is that I'm trying to find an app for my android phone that I can use to pull these text files from my dropbox account and read without having to add '.txt' onto the end of it. I have a bunch of text readers on my phone, but none of them open a plain text file without the '.txt' extension. I could simply put it on the end of each file I know, but I just don't want to. If push comes to shove I will but I wanna know more about it first to see if I can come up with a solution. 

Hope I make sense... :) Any thoughts / links / comments / jokes are appreciated.

---

### Post by nothingspecial on 2011-07-19
The people of Dubai never watch "The Flintstones"......

...... but the people of Abu Dhabi do.

That was the joke...

File extensions are not necessary in linux, although they can help organise things. The fact that your android app won't read them is a limitation of the android software.

Not much you can do other than find a text reader that will recognise a text file without an extension.

---

### Post by Herman on 2011-07-19
An excellent question.

If you type the following in a terminal, it will tell you a little part of your answer,
```
man file
```A little more of the answer is explained in this link, [Magic number (programming)]("http://en.wikipedia.org/wiki/Magic_number_%28programming%29") - wikipedia.

And still more of the answer can be found in this other link, [File Format]("http://en.wikipedia.org/wiki/File_format#Magic_number") - wikipedia.

As a point of interest, besides the use of file name extensions, there's another difference in the format of plain text file between Windows and Linux that we need to be mindful of too.
When we're using a Gnu/Linux operating system we can easily open and read a plain text file no matter whether it was made in Windows or in Gnu/Linux, but Windows users have trouble reading plain text files made in Linux.
They open as one big long line of text and you need to scroll sideways all the way to read them.

That's because the newline character for Linux and other Unix-like systems is LF but Windows uses CR+LF.
There's a small program we can install called dos2unix we can install and that can be used to make text file made in Linux Windows compatible. 
For example if we try to edit the boot.ini file to fix an unbootable Windows XP computer using Ubuntu or a Ubuntu Live CD, it will be okay if we only edit the right numbers.
If we try too much fancy stuff though and press our return key (or enter) and thus write a Linux newline character to the file, Windows will not boot and it will consider the boot.ini to be corrupted, even though it looks fine from Ubuntu.

I'm interested to learn what kind of text files Android can read, I imagine it would handle text files in the Linux manner since I read somewhere that Android uses a Linux Kernel, (if I'm not mistaken, or one modeled after the Linux kernel)? I read the newer Andriods use the ext4 file system too.
I do know that Google makes .kml file which can be read and edited easily in Ubuntu but just look like one big long single sentence in Windows making .kml programming impossible. I don't know how Windows users get around that if they want to try out .kml programming.

links: [Newline]("http://en.wikipedia.org/wiki/Newline") - wikipedia, and [Unix2dos:]("http://wei-jiang.com/system/unix/unix2dos-converts-linux-and-macintosh-files-to-windows-format") Converts Linux and MacIntosh Files to Windows Format.
 :)

---

### Post by decrepit on 2011-07-19
I share a lot of my data with windows, so whenever I save/name a file I add the appropriate extension. It's not hard to add .txt to the file name when you save it. (Just have to remember to do it)

And I think, in windows, if you use wordpad instead of notepad, it retains the line structure.

---

### Post by CatKiller on 2011-07-19
[A bit about why file name is a ridiculous way of identifying file type]("http://arstechnica.com/apple/reviews/2001/08/metadata.ars/1").

Microsoft shackled themselves and their users to having the last three characters of a file name being somehow magical. Then they tried to hide these magical characters, leading to bigboobies.jpg.exe and other wonders for the user.

Any application that can only use file name to determine file type is broken and should be rejected. For the most part, GNU/Linux doesn't need such aberrant mechanisms (.desktop files, I'm glaring at you) so it doesn't use them. File names are a convenience for the user. They aren't magical.

---

### Post by FormatSeize on 2011-07-19
> **Scooter_X said:**
> I have a bunch of text readers on my phone, but none of them open a plain text file without the '.txt' extension.
This is because the OS on your phone is set up to recognize file extensions as a necessary aspect of a file. As was already said, file extensions are largely a waste of time in Linux and they aren't used as a necessary characteristic of a file. As such, your phone doesn't open them because it does not know how to handle files without a flag telling it what type of file it is.

---

### Post by AlphaLexman on 2011-07-19
Blame Google.

Even google docs **cannot** open a basic text file (you have to download it) with or without the .txt extension.

*Android is a google product.*

---

