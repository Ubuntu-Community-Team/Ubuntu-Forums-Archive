---
title: "Installing Banshee Plugins from CVS"
date: 2006-06-05
forum: General Help
---

### Post by souteneur3190 on 2006-06-05
svn co svn://svn.banshee-project.org/trunk/banshee-official-plugins

That is what I am told to type in to ger banshee plugins but unfortuantely I get this:

bash: svn: command not found

I have absolutly know idea what to do.  Please Help

Here is the page where I am getting this from, all I want to is download some banshee plugins.

[http://patches.ximian.com/PluginRepository](http://patches.ximian.com/PluginRepository)

---

### Post by souteneur3190 on 2006-06-05
svn co svn://svn.banshee-project.org/trunk/banshee-official-plugins

That is what I am told to type in to ger banshee plugins but unfortuantely I get this:

bash: svn: command not found

I have absolutly know idea what to do. Please Help

Here is the page where I am getting this from, all I want to is download some banshee plugins.

[http://patches.ximian.com/PluginRepository](http://patches.ximian.com/PluginRepository)

---

### Post by Nordoelum on 2006-06-05
Have you installed svn or subversion as it is called?

---

### Post by souteneur3190 on 2006-06-05
i assume that i didnt since i have no idea what that is

---

### Post by manicka on 2006-06-05
sudp apt-get install subversion

---

### Post by souteneur3190 on 2006-06-05
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build banshee-official-plugins
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

what in thr world is that?>

---

### Post by GameGod on 2006-06-05
It looks like you don't have any of the build/compilation tools installed.
Try a:
sudo apt-get install build-essential

Hopefully that'll get you through the build process... The banshee plugins might be a bit tricky to try installing by hand if you're new to this, but there's no better way to learn than by diving right into it. ;)
Good luck! :)

---

### Post by epikos on 2006-06-19
I too am trying to compile some banshee code from CVS. In my case, I'm trying to build Banshee its self because I need iPod support, and the CVS/HEAD 0.11.0 code is required for the iPod plugins. Anyway, I've got build-essential installed, along with cvs and subversion.


When I execute:
./autogen.sh --prefix=/usr

I get:
Checking for required M4 macros...
  gnome-compiler-flags.m4 not found
  libtool.m4 not found
  glib-gettext.m4 not found
  intltool.m4 not found
  pkg.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build banshee
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

Sounds similar to what the OP is seeing, or was seeing. 
Anyone have any thoughts on this? Thanks!

---

### Post by Grundlebug on 2006-06-30
My iPod nano is supported just fine with the version of Banshee that I got from the dapper repositories.

Are you sure you need to compile some code to get your iPod up and running?

---

### Post by soulfire on 2006-07-05
[QUOTE=epikos]
When I execute:
./autogen.sh --prefix=/usr

I get:
Checking for required M4 macros...
  gnome-compiler-flags.m4 not found
  libtool.m4 not found
  glib-gettext.m4 not found
  intltool.m4 not found
  pkg.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build banshee
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?
[/QUOTE]

I am facing the same problem trying to compile some Rhythmbox CVS code.
Any idea? :(

**EDIT**
Solution suggested here [http://www.ubuntuforums.org/showpost.php?p=1163753&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1163753&postcount=3)
worked for me

---

