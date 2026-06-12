---
title: "Should/Can Wine install a Windows Java program?"
date: 2012-01-06
forum: General Help
---

### Post by wh33t on 2012-01-06
So I'm still working on making the switch. I'm now using the latest Ubuntu with Unity. 

I'd like to install this old PHP-IDE that I use on Windows. Call me old fashioned, but this program works the way I like to work so I'd like to take it along with me into Linux land as well. 

The program we are talking about is Zend Development Environment 5.2.0 . This program requires the JRE so is this a simple case of just installing the JRE into my Wine environment and then installing the Program? I've tried to install Zend Development Environment and it didn't work. What happens is the install Wizard appears but as soon as click NEXT it doesn't redraw the window and it halts. 

Any tips in the right direction would be awesome as I can't leave Windows if I can't install this program.

---

### Post by jwbrase on 2012-01-06
No need to mess with Wine: Zend is available for Linux.

---

### Post by wh33t on 2012-01-06
Are you sure? I haven't ever been able to find a Linux version of 5.2.0. Can you send me some links or something? Really appreciate it!

---

### Post by jwbrase on 2012-01-06
Oh, you want a particular version? That I can't help you with. I just looked it up and noticed it had a Linux version.

Is there any reason you can't/won't use the most recent version?

---

### Post by wh33t on 2012-01-06
> **jwbrase said:**
> Oh, you want a particular version? That I can't help you with. I just looked it up and noticed it had a Linux version.

Is there any reason you can't/won't use the most recent version?

Yea, it is completely different. It uses the Model View Controller system and actually forces you to use the Zend Frame work. The older IDE which I want to use functions a lot like Dreamweaver used too. It's what I'm used to.

---

### Post by Chronon on 2012-01-08
Does it not work running with JRE installed in Ubuntu?

---

### Post by wh33t on 2012-01-08
> **Chronon said:**
> Does it not work running with JRE installed in Ubuntu?

I'm not sure. Is JRE installed out of the box and would it be running on boot? If so, then no.

---

### Post by Chronon on 2012-01-08
I'm not sure if it's installed by default.  You can always check to be sure.  Do other java programs run?

---

### Post by 1clue on 2012-01-08
Speaking as one developer to another, is there some particular app you're maintaining that won't work on some other version or IDE?

Please don't take this post badly, I know it could be read as preaching and I'm just trying to offer advice, not tell you what you have to do.

The reason I'm saying it is I've been programming professionally since the late 80's.  There is no longer any viable hardware which will run the development system I started on (which was on a CDC Cyber 170 mainframe), and if there were I wouldn't want to use it because my phone is faster, has twice as many cores, is more reliable and several orders of magnitude easier to use.

If there's a genuine reason to stay with the same old IDE -- like an indispensable legacy app that isn't worth moving to a new technology -- then I recommend that you start exploring alternatives or you'll be caught with your pants down.

Over the years I've tried multiple strategies toward productivity.  First was to stick with what I know, which didn't last more than a few years.  Second was to try every latest thing that came out, which was expensive because at the time IDEs were not free at all.  Third and best was to dip a toe into the water of each new IDE I came across, and then use whichever one seemed best adapted to whatever project I was working on at the time.

Oddly enough, after I picked method 3 (which I'm still using) I spent the longest time I ever had on a single editor.  I used vi/vim for over 10 years, and skipped over a bunch of IDEs which everyone used except me.  Occasionally I would switch to an IDE for some particular task but for the most part I found Vim's functionality to be handier and faster.

Currently I use STS or Vim or TextMate (on a Mac) but I take a look at lots of different tools depending on what the project is.

Good luck and have fun.

---

### Post by wh33t on 2012-01-08
> **Chronon said:**
> I'm not sure if it's installed by default.  You can always check to be sure.  Do other java programs run?

Not sure. I know there is a command to check whether or not JRE is running but I can't remember it.

---

### Post by wh33t on 2012-01-08
> **1clue said:**
> Speaking as one developer to another, is there some particular app you're maintaining that won't work on some other version or IDE?

Please don't take this post badly, I know it could be read as preaching and I'm just trying to offer advice, not tell you what you have to do.

The reason I'm saying it is I've been programming professionally since the late 80's.  There is no longer any viable hardware which will run the development system I started on (which was on a CDC Cyber 170 mainframe), and if there were I wouldn't want to use it because my phone is faster, has twice as many cores, is more reliable and several orders of magnitude easier to use.

If there's a genuine reason to stay with the same old IDE -- like an indispensable legacy app that isn't worth moving to a new technology -- then I recommend that you start exploring alternatives or you'll be caught with your pants down.

Over the years I've tried multiple strategies toward productivity.  First was to stick with what I know, which didn't last more than a few years.  Second was to try every latest thing that came out, which was expensive because at the time IDEs were not free at all.  Third and best was to dip a toe into the water of each new IDE I came across, and then use whichever one seemed best adapted to whatever project I was working on at the time.

Oddly enough, after I picked method 3 (which I'm still using) I spent the longest time I ever had on a single editor.  I used vi/vim for over 10 years, and skipped over a bunch of IDEs which everyone used except me.  Occasionally I would switch to an IDE for some particular task but for the most part I found Vim's functionality to be handier and faster.

Currently I use STS or Vim or TextMate (on a Mac) but I take a look at lots of different tools depending on what the project is.

Good luck and have fun.

That is great advice man. I know the reality that I can't stay where I'm comfortable forever, and nor should I. That's part of the reason why I'm trying to move from Xp to linux. I use this particular IDE because it works the way that I work. I'm sure there are other IDE's out there but how many of them will run on Linux and do what I need them too. It seems like very few unfortunately. 

When I program I like to use both mouse and keyboard. I like to highlight chunks of text to move them here and there and that's why I don't use VI/VIM. I also like to do the remote editing of files which isn't that easy with VI/VIM in terms of opening multiple files and such.

---

### Post by 1clue on 2012-01-08
> **wh33t said:**
> That is great advice man. I know the reality that I can't stay where I'm comfortable forever, and nor should I. That's part of the reason why I'm trying to move from Xp to linux. **I use this particular IDE because it works the way that I work.** I'm sure there are other IDE's out there but how many of them will run on Linux and do what I need them too. It seems like very few unfortunately.


I hear you.  The part I bolded is profound IMO.  There are other development environments out there, but one of the big problems I've had with them over the years is that they try to dictate how you should work.  Eclipse was the first one I had found that was sufficiently better than Vim that I felt it was worth learning.  STS is a good one too, of course it's based on Eclipse.

I don't have experience with PHP but I have been developing in Java for the past 12 years or more.  For Java and other statically linked languages an IDE really makes a lot of sense, but lately I use Groovy/Grails, and that lets you inject code at runtime or compile at runtime.  Half of an IDE's benefit is navigating to the procedure/method/function implementation, and that just doesn't work with Groovy.

I'm back to finding really good editors, which is a lot easier than finding a really good IDE, and a good set of tools to help do what you do.  When I started using Linux, XFree86 was unstable and fit into the category of novelty or entertainment or massive waste of time rather than an indispensable part of an operating system.  I learned the command line tools first, and frankly I still use them as much as or more than the GUI ones.

There is absolutely no guarantee that Linux has an IDE that suits your style, but I will lay good odds there is a really really good editor out there.

> 
When I program I like to use both mouse and keyboard. I like to highlight chunks of text to move them here and there and that's why I don't use VI/VIM. I also like to do the remote editing of files which isn't that easy with VI/VIM in terms of opening multiple files and such.

In a terminal window, you highlight the text and it's automatically copied to the X clipboard, and you center click where you want it to go and that's paste.  I like it better than that control-c crap.  :)

I'm not gonna go off on a "vim can do everything" rant like I have at every opportunity for years and years.  Keep in mind that it's only been a few years that I've found an IDE worth switching from Vim.  Both Vim and Emacs are extremely capable command-line editors that have been around since the cathode ray tube came to computing.  Literally.  And they're still both in extremely wide use, and there are also some very good GUI-only programming editors out there.

Rather than recommending a GUI programming editor, I'm going to let the proponents of those editors chime in.

One thing I will strongly recommend is that, if you intend to stick with Linux, you get really good with regular expressions.  A lot of Linux makes strong use of them, and if there seems to be a lack of editors with some sort of functionality it's quite possible that there's a simple and fast regex technique that performs that operation.

Good luck and have fun.

---

### Post by wh33t on 2012-01-10
> **1clue said:**
> I hear you.  The part I bolded is profound IMO.  There are other development environments out there, but one of the big problems I've had with them over the years is that they try to dictate how you should work.  Eclipse was the first one I had found that was sufficiently better than Vim that I felt it was worth learning.  STS is a good one too, of course it's based on Eclipse.

I don't have experience with PHP but I have been developing in Java for the past 12 years or more.  For Java and other statically linked languages an IDE really makes a lot of sense, but lately I use Groovy/Grails, and that lets you inject code at runtime or compile at runtime.  Half of an IDE's benefit is navigating to the procedure/method/function implementation, and that just doesn't work with Groovy.

I'm back to finding really good editors, which is a lot easier than finding a really good IDE, and a good set of tools to help do what you do.  When I started using Linux, XFree86 was unstable and fit into the category of novelty or entertainment or massive waste of time rather than an indispensable part of an operating system.  I learned the command line tools first, and frankly I still use them as much as or more than the GUI ones.

There is absolutely no guarantee that Linux has an IDE that suits your style, but I will lay good odds there is a really really good editor out there.



In a terminal window, you highlight the text and it's automatically copied to the X clipboard, and you center click where you want it to go and that's paste.  I like it better than that control-c crap.  :)

I'm not gonna go off on a "vim can do everything" rant like I have at every opportunity for years and years.  Keep in mind that it's only been a few years that I've found an IDE worth switching from Vim.  Both Vim and Emacs are extremely capable command-line editors that have been around since the cathode ray tube came to computing.  Literally.  And they're still both in extremely wide use, and there are also some very good GUI-only programming editors out there.

Rather than recommending a GUI programming editor, I'm going to let the proponents of those editors chime in.

One thing I will strongly recommend is that, if you intend to stick with Linux, you get really good with regular expressions.  A lot of Linux makes strong use of them, and if there seems to be a lack of editors with some sort of functionality it's quite possible that there's a simple and fast regex technique that performs that operation.

Good luck and have fun.

I forgot to update this. I actually managed to find a Linux binary of the editor I want to use :D So I'm using that now. w00t

---

