---
title: "very frusrated"
date: 2009-09-15
forum: General Help
---

### Post by gnilaeh on 2009-09-15
how can i gain total permission on ubuntu? i am the only user and i gat alot of...you dont have permission...trying to learn thos os. thx

---

### Post by NoaHall on 2009-09-15
What are you trying to do?

It's not ever a good idea to own anything other than your /home/ folder.

---

### Post by gnilaeh on 2009-09-15
trying to look at nvidia setting config.  it tells me to edit the X config ....nvidia xconfig.... as root. i us e the terminal dont i?

---

### Post by NoaHall on 2009-09-15
run "gksudo nvidia-settings" from the terminal. - that will let you save it :)

---

### Post by apmcd47 on 2009-09-15
If you really need to look at or edit something as root use *sudo*. To edit something use *sudoedit*. 

But be careful, and make sure you have backups. For example:
[PHP]sudo cp -p Xorg.conf Xorg.conf-[/PHP]

Andrew

---

### Post by NoaHall on 2009-09-15
Don't worry about what Andrew said - nvidia makes back ups for you. Although he's right about the sudo bit, although it should be "gksudo" for graphical apps.

---

### Post by Marlonsm on 2009-09-15
Files that are very important for the system, that if changed wrong may break it are only possible to modify with a root account. It's a matter of security, as you'll only have access to them if you have the root password and know what you're doing.

To open them there are some ways:
-In the terminal type:
```
sudo gedit <file location and name>
```
-Open Nautilus as root by typing:
```
gksu nautilus
```
(Be _extremelly_ careful doing it)
-Install the gksu-nautilus package (not sure if that's the name), that allows you to access the root mode by right-clicking Nautilus.

Usually there is no graphic interface for it because those files should only be edited if you know what you're doing.

---

### Post by gnilaeh on 2009-09-15
ok i think i get the jest of the posts. no need to mess with it. so how do i know what drivers i have and or need to update?  i installed a gme with play deb and trying to run itm it came up with an error, fatal error...somethig to do with 2d gl.

---

### Post by lduperval on 2009-09-15
Of course, you can always tell the system that whenever you run (gk)sudo, you don't want to be prompted for a password. 

L

---

### Post by gnilaeh on 2009-09-15
trying a different approach here.  if this is the wrong forum, i appoligize.
i`m tired of microsoft.  so last saturday i did a search for a different os to try. thats how i found ubantu. my main computer use is for gaming. looking for something other than everquest. how can i set up ubuntu for that? or should i look at a different os like kubuntu or whatever?  also is there a guide on commands and how to use them? that would be very helpful. 
thank for any input here.

---

### Post by steveneddy on 2009-09-15
For better results try using capitol letters where necessary.

Also spread out your message with spacing so it is easier to read.

Spelling helps but is not totally necessary.

You stated that you wanted something different than Everquest, and your next question is "How do I set up Ubuntu for that?"

For what? For not running Everquest? Could you be a little more descriptive about what you are actually trying to accomplish? do you want a gaming machine that runs Linux or do you just need to surf, check e-mail and play on MySpace and Facebook?

Look at the links in my sig and if you are interested in gaming there is a section dealing with gaming in particular on these forums. [Link]("http://ubuntuforums.org/forumdisplay.php?f=93")

Read and lurk around in the forums for a few days and try and absorb some of what you are looking at. This is a lot different than the Windows world you just left. 

Welcome to the community.

---

