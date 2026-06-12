---
title: "Chrome showing up as Prism shortcut in Docky"
date: 2011-01-19
forum: General Help
---

### Post by aaronmfisher86 on 2011-01-19
So I'm fairly newb-ish when it comes to linux and I've screwed something up and I have no clue how to fix it.  Hopefully someone will have an idea of where I should start looking.

That being said, here's what I did.

I wanted to make HootSuite (a webpage) always on the bottom and basically "stuck" to one of the workspaces on my desktop (basically recreate the "active desktop" feature that windows has).  First I made an Application Shortcut in chrome for the webpage that way I'd have a link on my harddrive that would open it up with just the site and no tabs or anything else.  Then I went into compiz and started changing a bunch of settings in Window Rules, Window Place and Window Decorations so when I opened the Application Shortcut created from Chrome it would show up without any decorations on the bottom layer of all my applications on the 3rd workspace.  I accomplished this task.  In trying to get it working I first had set all the window rules to run when a window class respective to chromium was open with the title HootSuite.  But then everytime I went to HootSuite in my browser the window rules would go into effect and that was annoying.  So I made a simple HTML file with a frame that would load HootSuite but would have the title of the webpage as a bunch of random numbers.  I then changed all my window rules accordingly and everything was working well.  So that's the back story, here's the problem...

Now everytime I open a window in chrome instead of showing the Chrome icon and title in docky it shows the icon of the application shortcut and HootSuite as the title.  I'm assuming in all the configuring and reconfiguring I did I messed up somewhere and a setting stuck that I didn't want to stick.  I've tried uninstalling docky and deleting all the settings in docky using this process
```
 killall docky
 rm -r ~/.local/share/docky
 rm -r ~/.cache/docky
 gconftool-2 --recursive-unset /apps/docky-2
```
which I found here:
[http://wiki.go-docky.com/index.php?title=Debug](http://wiki.go-docky.com/index.php?title=Debug)

but that didn't work.  The weird thing is that if I turn on the gnome window list applet it shows up with the correct icon and title there.

I'm so very confused.

Please Help! :oops:

P.S.  I've included a screenshot below to help explain the problem, the red arrow is pointing to the gnome window list and the yellow arrow is pointing the "bad icon" in docky

[IMG]http://lh6.ggpht.com/_ADw-lcAq9XE/TTeakV41jaI/AAAAAAAAB-k/ulpm-U_0hdE/s800/Screenshot-1.png[/IMG]

---

### Post by 123456789123456789123456 on 2011-01-19
had something simular happen when I was working with firefox once.  It is not the same as since firefox refused to load at all.  I fixed the problem by uninstalling firefox and reinstalling firefox.

With that link still on the computer, I would suggest uninstalling crome, and reinstalling it.  But don't do that until you hear from someone else, it may be a better fix out there.

---

### Post by ElHana0902 on 2011-02-07
man, i got the same problem, but instead of showing the prism icon, theres the bookmark manager shortcut, i already uninstalled docky and chrome thru the synaptic package but nothing seems to work... HELP US SOMEBODY!!!
and i dont want to use Avant >:\

---

### Post by ElHana0902 on 2011-02-07
I kind of solved it, I put a chrome shortcut on desktop and then move it to the docky. the only thing is that if you delete the shortcut of the desktop, the docky shortcut doesnt work...
hope someone finds a better way to do it...

---

### Post by ElHana0902 on 2011-02-07
try these steps, drag your chrome off the docky to delete it, then drag from the internet menu the chrome icon, and put it on docky, that will work (:

---

