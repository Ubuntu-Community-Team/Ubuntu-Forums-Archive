---
title: "Need To Install A .package File"
date: 2010-06-05
forum: General Help
---

### Post by Jakiejake on 2010-06-05
Hi,
I downloaded Yenka [http://www.yenka.com/en/Downloads/](http://www.yenka.com/en/Downloads/) and tried to open it
Turns out it is a .package file WHAT IS THAT
And how do I install it?
Please Help

---

### Post by Elfy on 2010-06-05
assuming it's on your Desktop

```

cd Desktop
chmod +x Yenk<tab>
./Yenk<tab>
```

---

### Post by Jakiejake on 2010-06-05
> **forestpiskie said:**
> assuming it's on your Desktop

```

cd Desktop
chmod +x Yenk<tab>
./Yenk<tab>
```

What do you mean? I have "Yenka_3.2.6.package" What do I do
I cd'ed to the desktop now what?

---

### Post by Jakiejake on 2010-06-05
> **forestpiskie said:**
> assuming it's on your Desktop

```

cd Desktop
chmod +x Yenk<tab>
./Yenk<tab>
```

Got It
> jacob@jacob-desktop:~/Desktop$ chmod +x Yenka_3.2.6.package
jacob@jacob-desktop:~/Desktop$ ./Yenka_3.2.6.package

The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): y

Attempting download of [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2) ... 

--2010-06-05 21:14:09--  [http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2](http://autopackage.org/downloads/latest/x86_64/autopackage.tar.bz2)
Resolving autopackage.org... 85.214.113.104
Connecting to autopackage.org|85.214.113.104|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-06-05 21:14:10 ERROR 404: Not Found.

Download failed.


Attempting download of [http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2) ... 

--2010-06-05 21:14:10--  [http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/latest/x86_64/autopackage.tar.bz2)
Resolving [www.wildgardenseed.com](www.wildgardenseed.com)... 66.40.65.97
Connecting to [www.wildgardenseed.com|66.40.65.97|:80](www.wildgardenseed.com|66.40.65.97|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www.wildgardenseed.com/autopackage/1.4.2/x86_64/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/1.4.2/x86_64/autopackage.tar.bz2) [following]
--2010-06-05 21:14:11--  [http://www.wildgardenseed.com/autopackage/1.4.2/x86_64/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/1.4.2/x86_64/autopackage.tar.bz2)
Reusing existing connection to [www.wildgardenseed.com:80](www.wildgardenseed.com:80).
HTTP request sent, awaiting response... 200 OK
Length: 919216 (898K) [application/x-tar]
Saving to: `autopackage.tar.bz2'

100%[======================================>] 919,216      383K/s   in 2.3s    

2010-06-05 21:14:14 (383 KB/s) - `autopackage.tar.bz2' saved [919216/919216]

Download completed.


tar: Record size = 8 blocks
................................................................................................

Your system is missing v5 of the C++ support library, putting a copy in /home/jacob/.local/lib


Attempting download of [http://autopackage.org/downloads/1.4.2/autopackage-gtk-1.4.2.package](http://autopackage.org/downloads/1.4.2/autopackage-gtk-1.4.2.package) ... 

--2010-06-05 21:14:29--  [http://autopackage.org/downloads/1.4.2/autopackage-gtk-1.4.2.package](http://autopackage.org/downloads/1.4.2/autopackage-gtk-1.4.2.package)
Resolving autopackage.org... 85.214.113.104
Connecting to autopackage.org|85.214.113.104|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-06-05 21:14:29 ERROR 404: Not Found.

Download failed.


Attempting download of [http://www.wildgardenseed.com/autopackage/1.4.2/autopackage-gtk-1.4.2.package](http://www.wildgardenseed.com/autopackage/1.4.2/autopackage-gtk-1.4.2.package) ... 

--2010-06-05 21:14:29--  [http://www.wildgardenseed.com/autopackage/1.4.2/autopackage-gtk-1.4.2.package](http://www.wildgardenseed.com/autopackage/1.4.2/autopackage-gtk-1.4.2.package)
Resolving [www.wildgardenseed.com](www.wildgardenseed.com)... 66.40.65.97
Connecting to [www.wildgardenseed.com|66.40.65.97|:80](www.wildgardenseed.com|66.40.65.97|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 316224 (309K) [application/x-autopackage]
Saving to: `autopackage-gtk-1.4.2.package'

100%[======================================>] 316,224      212K/s   in 1.5s    

2010-06-05 21:14:31 (212 KB/s) - `autopackage-gtk-1.4.2.package' saved [316224/316224]

Download completed.



# Preparing package: Autopackage Software Installer (GTK+)                      
# Checking for GTK+ user interface toolkit ... passed
# Checking for Glade user interface loader library ... passed
# Installing package: Autopackage Software Installer (GTK+) (package 1 of 1)    
# 100%[==================================================] Extracting
# Preparing executables...
# Installing GNOME 2 file type information...
# Installing GNOME 2 application registry entries...
# Installing file type information (MIME)...
# Installing KDE 3.x file type information...
# Registering file type assocations...
# Installing icons...
# Installing icon themes...
# Installing menu items...
# Copying files to /home/jacob/.local/share/autopackage-gtk/glade
# 100%[==================================================] Copying
# Copying files to /home/jacob/.local/share/autopackage-manager
# Copying files to /home/jacob/.local/libexec/autopackage-gtk
# Installing translated dictionary files...
# 100%[==================================================] Copying
# Installing executables...
# Updating package database...

The following package was successfully installed:
* Autopackage Software Installer (GTK+)

The following menu entry is now available:
* Manage 3rd party software (System)

This installation used 996.4 KiB (1020.3 kB) of disk space.


Remove this package by running package remove autopackage-gtk from the command line.


# # # # # # # # # # # #

Autopackage support code was installed.
Autopackage graphical interface installation was skipped.

# # # # # # # # # # # #

Thank you for your patience. Installation of your package will now proceed.
You should not have to install the autopackage support code again.

# # # # # # # # # # # #

Please run 'exec bash' in each terminal to update your path.

# # # # # # # # # # # #

./Yenka_3.2.6.package: line 360: package: command not found
jacob@jacob-desktop:~/Desktop$ 


---

### Post by Jakiejake on 2010-06-05
> **Jakiejake said:**
> Got It

Now What?

---

### Post by Jakiejake on 2010-06-05
> **Jakiejake said:**
> Now What?

Tried Again
> jacob@jacob-desktop:~/Desktop$ chmod +x Yenka_3.2.6.package
jacob@jacob-desktop:~/Desktop$ ./Yenka_3.2.6.package
./Yenka_3.2.6.package: line 330: package: command not found
jacob@jacob-desktop:~/Desktop$ 

What do I do?

---

### Post by Jakiejake on 2010-06-05
> **Jakiejake said:**
> Got It

Found this
[http://autopackage.org/howtoinstall.html](http://autopackage.org/howtoinstall.html)
It works now but it says
> Error: 'Yenka' requires a global installation. Restart installation as super user (root).
Should I enable root?

---

### Post by Elfy on 2010-06-05
Looks like there's an error in the package.

Doesn't look like there's much information floating about for it either - maybe get in contact with the devlopers - sorry can't be of more help.

---

### Post by Elfy on 2010-06-05
> **Jakiejake said:**
> Found this
[http://autopackage.org/howtoinstall.html](http://autopackage.org/howtoinstall.html)
It works now but it says

Should I enable root?

Try with sudo 

```
sudo ./Yenk<tab>
```

---

### Post by Jakiejake on 2010-06-05
> **forestpiskie said:**
> Try with sudo 

```
sudo ./Yenk<tab>
```

I got this
> Error: 'Yenka' requires a global installation. Restart installation as super user (root).

---

### Post by Elfy on 2010-06-05
It installed here without issue and without sudo. So I don't know why it's requiring it from you.

I also didn't get any errors - maybe some corruption in the download. 

Try redownloading it.

Ed it - The package installer asked for the password a couple of times - but I didn't actually need to run sudo ./Ye...

---

### Post by Jakiejake on 2010-06-05
> **forestpiskie said:**
> It installed here without issue and without sudo. So I don't know why it's requiring it from you.

I also didn't get any errors - maybe some corruption in the download. 

Try redownloading it.

How?

---

### Post by Jakiejake on 2010-06-05
THANKS!
I ran > remove autopackage-gtk Then your commands in SU (Super User) and it is installing now! :)

---

### Post by Elfy on 2010-06-05
Cool - glad I could help - just so you know - you'll be able to remove it by using the Managae 3rd Party Software Tool which should be in your System Tools menu - I went through the install and remove as I don't actually want the thing here ;)

---

### Post by Jakiejake on 2010-06-05
> **forestpiskie said:**
> Cool - glad I could help - just so you know - you'll be able to remove it by using the Managae 3rd Party Software Tool which should be in your System Tools menu - I went through the install and remove as I don't actually want the thing here ;)

Cool
Marked as solved!

---

### Post by srekkas on 2011-01-31
Helo. I have ubuntu 10.04. I installed Yenka software. It runs, but i get constant flisckering then in workspace . Video Ati mobility 3470.

---

