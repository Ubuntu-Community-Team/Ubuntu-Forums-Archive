---
title: "How to uninstall compiled(non deb) programs?"
date: 2006-06-07
forum: General Help
---

### Post by Dalik on 2006-06-07
I love Ubuntu package management tools but I do find myself trying applications that are not updated for example, mono developer 11 were the repos are up to version 10.

I installed the package from source and I ran into a few issues(it loaded once and wont load again) so I wanted to uninstall it but the files are kinda placed in different area's not many but a few and I wanted to know if there was an uninstall command that I can issue to uninstall a packaged that I compiled?  This isnt a mono question but in general is there a command and or process that a normal linux user can do to uninstall compiled from source packages?

Some packages can be large and all over the place and I dont think deleting the files and taking off the service if any from the list to be a good way to doing things.

Thank you.

---

### Post by andrecasteliano on 2006-06-07
Go to folder where are compiled sources (where you 'untar' program source package) and type:

sudo make uninstall

Should work.

Regards,

André Casteliano

---

### Post by Dalik on 2006-06-07
Ok I copied the extracted source folder from the trash bin to my desktop and ran that command it and seemed to work fine.

Now my question is, do I need to keep a copy of the source files and or compressed tar.gz file to uninstall it?  This should be fine for me but I am thinking of people searching for an answer to this kind of problem.

Would be nice to uninstall it without having to keep a copy of the tar.gz file laying around.

Cheers.

---

### Post by xtacocorex on 2006-06-07
You can always install checkinstall from the repos so when you compile you can do this:
```
./configure && make && sudo checkinstall
```
and this will make a .deb package for you that is easy to remove from the system with:
```
sudo dpkg -r <package name>
```

Then you can remove the source .tar.gz from your computer. You will have to do:
```
sudo chown <username> <package name>.deb
```
in the source directory to make it yours and the move that to another location so that you have it on hand if you need it, then you can delete the source folder.

You might have to change ownership of 2 other files, but that also depends on how you do the checkinstall options when it runs.

---

### Post by Dalik on 2006-06-07
Ok that is sexy!

Thanks for that, I am installing it now.

Cheers.

---

### Post by thasheep on 2006-06-07
It's a good idea to create deb packages that can be installed like the rest of the system. There are guides around the place (sorry for not being more specific).
If you're being lazy and don't want to create a package, it's a good idea to install everything you build yourself to /usr/local (ie, don't do '--prefix=/usr' when configuring). This way it won't get messed up with everything that came with the system.
If you find you have deleted the unpacked source, you can always unpack it again, run configure again (with the same options as before) and then 'make uninstall'.
Also, unfortunately, not all Makefiles support 'make uninstall' so again, it's best to create a .deb.

---

### Post by Dalik on 2006-06-07
I thought "/opt" was for installs that shouldnt mess with the system, or user installed packages?

I just did ./configure --help and saw in the example that the default location is infact /usr/local/*

so just running "./configure" will install to /usr/local/*   ?

I will look at creating a .deb package from tar.gz files or however its done, I think this checkinstall will work perfect in most cases.

Thank for the tips.

---

### Post by xtacocorex on 2006-06-07
[quote="Dalik"]I just did ./configure --help and saw in the example that the default location is infact /usr/local/*[/quote]

The default location (prefix) also depends on the developer who wrote the program. I've compiled many a program in Fedora that just went all over the system because of this.

> so just running "./configure" will install to /usr/local/* ?
For this program, yes, but for others, it might do /usr.

> I thought "/opt" was for installs that shouldnt mess with the system, or user installed packages?

I use /opt for programs that I can't compile, ie. ones that are distributed as binary tar files. But, that's just how I use /opt. I also do my configure with --prefix=/usr because I have a dislike for /usr/local for some odd reason. That may change after the info that thasheep gave.

---

### Post by Dalik on 2006-06-07
Ok I going to try to setup mono + monodevelop.
I used the package from the repos for mono 1.1.13 but the monodevelop ./configure said I needed mono 1.1.10 or higher installed.  I uninstalled it and going to try from source.

well see how it goes.

---

