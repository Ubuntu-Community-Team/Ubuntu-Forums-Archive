---
title: "Un-Invisible Mystery Not-Really-Here-at-All Files"
date: 2006-03-09
forum: General Help
---

### Post by dpaint4 on 2006-03-09
Hey guys. Before today I thought there were invisible files and visible files. Sometimes I'd need to show my invisible files to make little mods here and there, but mostly I just left them invisible, because that's the type of user I am.

Well today I was browsing for something through the directory tree to send a file via Thunderbird (this issue is not specific to Thunderbird, however), and I noticed that EVERY 'empty file' I'd ever created on the desktop is somehow leaving a mystery ghost file behind, where the name of the file is the name I'd originally given the file preceded by a tilda (~).  So, class_notes becomes ~class_notes.

These files are only visible through the directory tree, and showing or hiding 'invisibles' has nothing to do with them seemingly. I can only see them when I'm looking for an item through an application's file browser. (Not sure what to call that, but you know, like when you're saving, or loading something and you get to browse for a file or location? That's when they show up!)

What are they? Should I care? How can I get rid of them? They sure are going to pile up!

I just transitioned to Ubuntu (my first Linux) last weekend and it has been nothing but smooth sailing. Little things like this are the only bits that confuse me, and I'm really thankful for the awsome community. Thanks for the information.

---

### Post by bluevoodoo1 on 2006-03-09
Check out this thread
[http://ubuntuforums.org/showthread.php?t=138771](http://ubuntuforums.org/showthread.php?t=138771)

---

### Post by dpaint4 on 2006-03-09
[QUOTE=bluevoodoo1]Check out this thread
[http://ubuntuforums.org/showthread.php?t=138771](http://ubuntuforums.org/showthread.php?t=138771)[/QUOTE]

Thanks. That was helpful. But that guy's issue was never resolved in a way that I can understand.

The final 'answer' was:
[COLOR="Gray"]
You can:
1. instead of passing rm - v example.file, you can pass rm -v example.file example.file~
2. reconfigure your application so that not to do this (although I consider it a bad idea)[/COLOR]

'Instead of passing rm - v'? 'Reconfigure so that not to do this'?

I can tell that he knows what he's talking about, but I don't know what he's talking about, and I just want a way to periodically remove these 'backup' files. No point in keeping two of things that I know I won't be changing, right?

Anyone have a way to remove the ~files after they're no longer needed. Some kind of system-wide cleanup routine would be awsome, where all ~files are removed, if that's all they're there for.

---

### Post by dpaint4 on 2006-03-09
Can't do it throuh Terminal. It doesn't aknowledge that they're there. Seriously, it bugs me that there is this massive heap of invisible trash collecting on my desktop. I for sure won't be starting any new documents there in the future, but that dosen't help me with the ~files that are already there. I turned off the option in the text editor that was making them, but I'd like to find a way to eliminate the pile that's already there. It's not about disk space. It's about sanity.

Here's what happened in Terminal:
[COLOR="Gray"]curtis@ZXB:~$ rm /home/curtis/Dektop/'7z Useage Info~'
rm: cannot remove `/home/curtis/Dektop/7z Useage Info~': No such file or directory[/COLOR]

If I did something wrong, correct me. I'm new to command lines in general.

---

### Post by dpaint4 on 2006-03-09
K. Well I'm an idiot but that's what I come to these forums to discover.

Terminal worked. Was typing badly I'm sure or something, and now what that guy wrote makes sense even though it didn't when I found it *at all*.

So. Thanks and I'm leaving for a while because I am so embarrassed!

---

### Post by bluevoodoo1 on 2006-03-09
[QUOTE=dpaint4]So. Thanks and I'm leaving for a while because I am so embarrassed![/QUOTE]

oh no! Don't be embarrassed, I'm glad it has been resolved!

---

