---
title: "Cannot switch between workspaces, Alt+Tab not working, stuck to one workspace..."
date: 2009-06-29
forum: General Help
---

### Post by tushantin on 2009-06-29
Hello there! 

This problem wasn't there before, but I have no idea how it came up all of a sudden. I'm using Ubuntu Jaunty Jackelope. 

When I open up a few workspaces I'm stuck in my active one. I can ONLY click and right-click on that and cannot seem to click outside of it until I close it by pressing Alt+F4. Alt+Tab doesn't help in this situation. It's hella annoying, especially when I need to work on Synfig... When I minimize my window and right click on my desktop, it right clicks on my task manager instead. 

Further more, I do not have internet connection on my computer, so some of the solutions posted before do not seem to work. Also, I cannot seem to install packages that require some dependencies or something (yes, I made sure they were Jaunty specific). Everytime I try to install it says dependencies not found or something like that. Thus I do not even have Compiz on it. 

Any help please? 

Another thing; where can I get drivers for GeForce 9600 for Ubuntu?

---

### Post by mikewhatever on 2009-06-29
Alt+Tab
From what I understand, you used to switch between open windows/programs with Alt+Tab, and now it doesn't work. Is this behavior related to a certain program? Can it be that you've accidentally assigned Alt+Tab to a different action? I can't think of any intelligent reason for that problem, nor do I know what the 'task manager' is.

Dependencies and internet
Ubuntu is a very internet oriented OS. There is a way to install packages without internet connection, but it requires another connected Ubuntu machine. Generally speaking, all dependencies must be installed before the desired package. What do you want to install?

Compiz and GeForce 9600 driver
Compiz is installed by default, but you need the nvidia driver to run it. There is an automated installer, but it needs internet connection to download the driver with the dependencies, which means your only option is to install the driver manually.

---

### Post by tushantin on 2009-06-30
Oops! I meant "Taskbar", not "Task Manager", sorry. But for some reason when I booted up my PC again today it worked fine once again. I really have no idea what's going on, but I'm glad it's fine. 

As for the dependencies and updates, that's one problem I can't sold as long as I'm not connected to internet, I suppose. How do I manually install the dependencies and nVidia drivers? Where can I find them?

---

### Post by RobOrr on 2009-06-30
It will continue to be a pain to get a hold of dependencies until you get access to the internet. If you have access with another computer, and you know the name of the dependencies however, it's not too bad.

In the past when I had problems with my internet, I wrote the package name down, and googled it. You need the .deb file preferably, although some may come in tarballs (.tar.gz or .tar). Move them over onto the computer you wish to install them on and run them (or extract and follow instructions if they are a tarball).  The .deb file is best as it'll put all the files exactly where you need them.

---

### Post by tushantin on 2009-06-30
Oh I forgot, that's another problem I have.

Googling the name of the dependencies is not a problem. The problem is tarballs themselves. For instance, I downloaded some things I needed to install, and then I followed the instructions. Some needed to be compiled, while some others needed to be installed with some scripts. I followed the instructions accurately, but I was unable to either compile or install it...

---

### Post by mikewhatever on 2009-06-30
I've not tried it, but others seem happy enough.
[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia)

---

### Post by divyabdasar on 2010-06-07
I was working on compiz config settings. after disabling compiz settings ALT+TAB was not working. I read all the forum discussions , then got the solution for this. 

under:
System->Preferences->keyboard shortcuts
      Under: 
      Window Managment->Move between windows,using pop-up window---set the shortcut key as alt+tab. 

Then it worked.:):):)

Thank you opensource.. you just rock. thank u guys for sharing your knowledge.:):):)

---

### Post by tushantin on 2010-06-08
Ah that seems to help, although I'm using Karmic as of now. But thank you. XD

---

