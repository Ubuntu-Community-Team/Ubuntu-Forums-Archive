---
title: "Following directory structure shown by Nautilus"
date: 2010-12-26
forum: General Help
---

### Post by tg3793 on 2010-12-26
Hello,

I've read a couple other explanations to questions that were similar to mine. However I think to work my question this way will give me answers that will further clarify things for me. In Nautilus I can't seem to visually tell the difference between a folder that comes from a symlink and the 'actual' folder that contains the original files. I've been using Linux for just a few months now and can't quite get the hang of this.

I understand that (in Linux) the file structure really doesn't seem to be all that important. For instance I can create a "Projects" folder on my external drive so that it is "/media/SignatureMini/Personal/Proj" and then create a symlink to it in Nautilus so that it is "/home/user/Personal/Proj". But the problem is, if I am in nautilus I might (at first glance) think that is a duplicate that I had copied instead of simply a symlink. Of course if I am at "/home/user/Personal/" I can see that there is a shortcut there. But if I am already at "/home/user/Personal/Proj" my first inclination is to create a test file in the other directory and then refresh the other view and see if it appears there also.

Am I the only one with this problem? :-) Is there an easier way to understand this?

---

### Post by tg3793 on 2010-12-27
Ok, no one has answered so far but then maybe those looking at this think this is too basic and that I need to simply do my homework. To which I assure you that I have already spent a couple of hours on this. 

And thusfar have only come up with **readlink** as a possible solution though not the solution I'm looking for because I want to know what the true path is from within Nautilus.

Any help is appreciated. Thank you.

---

### Post by matt_symes on 2010-12-27
Hi

In Nautilus, symbolic links have arrows on the folder or file.

Have a look at the screen shots below. DD is a symbolic link to a folder and the files in the other screen shot are links to files.

Kind regards

---

### Post by QLee on 2010-12-27
[QUOTE=tg3793]...
I understand that (in Linux) the file structure really doesn't seem to be all that important.[/QUOTE]

In my opinion, the filesystem structure is not only important, it is crucially important.


 [QUOTE=tg3793]For instance I can create a "Projects" folder on my external drive so that it is "/media/SignatureMini/Personal/Proj" and then create a symlink to it in Nautilus so that it is "/home/user/Personal/Proj". But the problem is, if I am in nautilus I might (at first glance) think that is a duplicate that I had copied instead of simply a symlink. Of course if I am at "/home/user/Personal/" I can see that there is a shortcut there. But if I am already at "/home/user/Personal/Proj" my first inclination is to create a test file in the other directory and then refresh the other view and see if it appears there also.
...[/QUOTE]

You do not create a link in nautilus per se (unless you are referring to a bookmark), you create a link in /home/user/Personal/ that links to /media/SignatureMini/Personal/Proj/ (your "Projects folder") and that link is named "Proj". The "files" you are looking in the "linked" directory are the real files, any actions that you do on them really happen, I'm not sure why you might consider them "duplicates" since you set up the structure yourself.

But, yes, you could create a file named, 01_these_are_real_files, in your "Projects folder" which might help you to remember. (01 to keep it at the top where you are likely to see it)

---

### Post by tg3793 on 2010-12-30
Thanks guys. Your responses to my problem are helping me think this through.
For further clarification I followed [matt_symes]("http://ubuntuforums.org/member.php?u=1067998") lead and attached a pic.

As you can see it looks like these two folders could be duplicates of each other:
"/home/scribe/Dropbox/Projects/Clients/Sudaan Carter/site"
"/home/scribe/Dropbox/sites/sudaan_carter/Project Sudaan/site"

And it's not until I create something in one directory and see it "magically" appear in the other directory that I'd find out it is the exact same folder.

> **QLee said:**
>  I'm not sure why you might consider them  "duplicates" since you set up the structure yourself. 

Because I sometimes (maybe once every couple of months) run across a 'real' duplicate that has found it's way into my directory structure. And when I'm zipping my way through my file structure at a hundred miles and hour I'm prone to think something like (what is represented in the pic I've attached) is something that needs to be deleted.

Maybe everyone else does a better job of remembering all of the symnlinks they've created :-)

---

### Post by matt_symes on 2010-12-30
Hi

What happens when, on both directories shown in your pics, you navigate up to the parent directories?

Does one of them show a link and the other not?

Kind regards.

---

### Post by tg3793 on 2011-01-29
Sorry for getting back to this thread after such a long time. But perhaps it was good since it helped me to think and experience something else related to this. This, "I fear", is going to reveal my newbieness :-)

Continuing off the logic that I began this post I decided to take it to the command prompt and see what happens. Low and behold:

:[COLOR=SeaGreen]~/Projects/Clients/Sudaan Carter/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/HTML$ [/COLOR]

LOL I could have kept going but I'm sure my point is clear ... I happen to know that the directory should be "[COLOR=SeaGreen]~/Dropbox/sites/sudaan_carter/HTML$[/COLOR]" which is a whole lot shorter way to get there. But I have a two symlinks that go from "site" and "Project_Sudaan".

Is this really the way that the OS functions? Even doing a pwd at the prompt does not reveal what I 'think' should be the absolute file path?

---

### Post by vanadium on 2011-01-29
The power of Linux symbolic links is that they let you arrange the file structure in a way that is convenient to you. Once created, they feel and behave as a real directory to the user.

---

### Post by tg3793 on 2011-01-31
Is there a Linux command that shows me the 'actual' directory along the sentiments of "the quickest way to something is to follow a straight line" ?

I originally thought that the PWD command was going to do that for me but it only tells me how I got to where i am. In my previous example I would like to have a command that showed me "[COLOR=SeaGreen]~/Dropbox/sites/sudaan_carter/HTML$[/COLOR]" when I am at "[COLOR=SeaGreen]~/Projects/Clients/Sudaan Carter/site/Project  Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project  Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project  Sudaan/site/Project Sudaan/site/HTML$"[COLOR=Black]

Hope I'm not thinking 'too' Windowy :-)

Thanks.
[/COLOR][/COLOR]

---

### Post by vanadium on 2011-01-31
pwd does that: show where you are.

If you navigated to "~/Dropbox/sites/sudaan_carter/HTML$" it will show "~/Dropbox/sites/sudaan_carter/HTML$"

If you navigated to ""~/Projects/Clients/Sudaan Carter/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/HTML$" it will show ""~/Projects/Clients/Sudaan Carter/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/Project Sudaan/site/HTML$"

This cannot be more straightforward and user friendly than that.

---

### Post by tg3793 on 2011-01-31
> **vanadium said:**
>  This cannot be more straightforward and user friendly than that.

Ok let me try framing this problem another way. If I did a search for a letter to my mother; say an "ls | grep letter2mom" and it was found; what "path" would the Linux file system report was the location to that file.

And if the Linux file system 'would' report a path to that file then how could I get 'that' sort of a path statement information short of doing some sort of "find" or "locate" or locate command.

To go back to my previous example, I'm applying it to a 'directory' now, if I had originally created an "HTML" directory at "[COLOR=SeaGreen]~/Dropbox/sites/sudaan_carter/HTML$[/COLOR]" and then I navigate to "[COLOR=SeaGreen]~/Projects/Clients/Sudaan  Carter/site/Project  Sudaan/site/Project Sudaan/site/Project  Sudaan/site/Project  Sudaan/site/Project Sudaan/site/Project  Sudaan/site/Project  Sudaan/site/Project Sudaan/site/HTML$"[/COLOR], is there a command that I can issue at the CLI that would tell me that "[COLOR=SeaGreen]~/Dropbox/sites/sudaan_carter/HTML$[/COLOR]" is the most direct way to that location?

Or maybe my above example doesn't represent an example that is true enough to a "real world" example.

Let's try this.
If I had two directories: 
"[COLOR=SeaGreen]~/Projects/Clients/Sudaan  Carter/site/HTML[/COLOR]"
<and>
 "[COLOR=SeaGreen]~/Dropbox/sites/sudaan_carter/HTML[/COLOR]"

And I 'knew' that one of them was a shortcut of the other ... then how would I be able to determine which which one was the 'original' path?

I'm I making any sense? ... I'm pretty sure I'm just missing something because of my newness to this file system.

---

### Post by mcduck on 2011-01-31
> **tg3793 said:**
> 
Let's try this.
If I had two directories: 
"[COLOR=SeaGreen]~/Projects/Clients/Sudaan  Carter/site/HTML[/COLOR]"
<and>
 "[COLOR=SeaGreen]~/Dropbox/sites/sudaan_carter/HTML[/COLOR]"

And I 'knew' that one of them was a shortcut of the other ... then how would I be able to determine which which one was the 'original' path?

I'm I making any sense? ... I'm pretty sure I'm just missing something because of my newness to this file system.
```
ls -l ~/Projects/Clients/Sudaan\ Carter/site/HTML
```
ls -l will tell you if it's a directory or a link. So does anything that tells you permissions (directory permissions start with a "d", link permissions start with "l")

Also you should be able to figure that out directly from the normal 'ls' output if you have a color terminal, since directories and symlinks will show with different colors (by default a directory is blue text, while a symlinked directory shows as cyan text).

---

### Post by tg3793 on 2011-01-31
At this point I should <insert synaptic response here> because I "knew" that. 

But then yes it's my newness flaring up ... The moment that I read your instructions about the colors I started to think to myself "duh" because I've been looking at that and 'using' that several times this week while logged into my server over SSH. 

Hear the echo ... duhhhhhh ! 
It must be time for a nap.
Thank you for your patience.

---

### Post by tg3793 on 2011-04-28
I decided to add this one last post to my thread because I had a similar navigational question that was truly [cleared up in this thread]("http://ubuntuforums.org/showthread.php?t=1741362"). Low and behold if I **create "a Launcher"** to something, then the directory structure always stays the same and I can mentally juggle it a lot better.

I don't fault anyone for not thinking about this solution in this thread. Because frankly I didn't word my problem in such a way that would have easily led anyone to this solution. ... Happy camper here; pitching tent.

---

### Post by tg3793 on 2011-06-17
This is related to a great deal of what I had in mind when I was struggling with this several months ago. 

Hope this helps someone else as well. I found a very cool script on Fresh Meat (call [nautilus-follow-symlink]("http://freshmeat.net/projects/nautilus-follow-symlink")) that would add a context menu entry to nautilus on symbolic links pointing to directories, which once clicked opens the pointed directory (the real path) in a window. 

This lead me to the original thought I had where there must be a command that would reveal this path without having to follow it.

---

