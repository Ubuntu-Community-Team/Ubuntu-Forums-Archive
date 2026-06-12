---
title: "Why won't some programs start up? Nothing happens when they are clicked."
date: 2012-03-24
forum: General Help
---

### Post by needhelplinux on 2012-03-24
I am using ubuntu linux 11.04. I installed lubuntu-core and am in the lubuntu version right now.

My computer is an hp pavilion a620n with an amd athlon xp 3200+ processor and I have recently changed the ram from 512 MB to 2 GB.

Some programs aren't starting recently. I am trying to use a program called "StencylWorks" from [http://stencyl.com](http://stencyl.com), but it won't start anymore. It used to start months ago. I haven't used it in a while and now that I try again, it won't work. I click the shell script to start it and then I press "execute", but nothing happens. The only thing I know that changed since I last used it was adding more ram.

I tried to update java, but it still won't start.

I have OpenJDK java and it is now at version (6b22-1.10.6-0ubuntu1)

I also have Sun's version of java, and I updated it to version 6 update 31.

I am trying to use a different program from [www.en.compilgames.net/index.php]("http://www.en.compilgames.net/index.php"), but the shell script won't start either and neither will the actual executable file for the program.

I checked the properties and they are all allowed to run as executable files.

There is also another problem, but I don't know it if is related. The program Blender from [http://www.blender.org/](http://www.blender.org/) always starts, but the menus are messed up. Some options like the top menu bar (file, edit, etc) don't show up, but I click in that area and the submenus do come up. A lot of things are messed up in that program. (I don't know how to use that program, so I am not sure if anything works at all. Blender was messed up  even before I changed the ram)

What could be the problem? Why was the stencylworks program working a few months ago and now it won't start? Why is blender always messed up?

Thank you for any help.

EDIT:

If I log back into Ubuntu instead of Lubuntu, the stencylworks program works again. Why would it not work in Lubuntu? Is it because I only installed "lubuntu-core" instead of the full version? Blender is still messed up in ubuntu though. The program at [http://www.en.compilgames.net/index.php](http://www.en.compilgames.net/index.php) still won't start, but I don't know if that's because of linux or because the program itself is messed up.

Does anyone know why blender would be messed up? Could it be a graphic card problem? I don't have a good one installed. I only have the kind that comes with all computers (integrated).

---

### Post by Roter1337 on 2012-03-24
why not try
sudo add-apt-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install --no-install-recommends lubuntu-desktop

---

### Post by CapnKirk on 2012-03-25
This may not help in your exact situation. But when I have problems with programs not starting when clicked in the UI, I then bring up a terminal command line and execute the program that way. If the program has the option, I turn on debug or verbose messages. Often, if there are path problems with java or problems with the UI widgets or whatever, the program will send error messages to standard error in the terminal. That can provide clues to the problem.

Hope this helps.

Kirk

---

