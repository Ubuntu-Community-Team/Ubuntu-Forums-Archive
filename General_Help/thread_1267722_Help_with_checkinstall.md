---
title: "Help with checkinstall"
date: 2009-09-16
forum: General Help
---

### Post by onespeedbiker on 2009-09-16
I am trying to create a .deb from a tar.gz file with checkinstall. Here are the instructions..

1 Install Checkinstall check

2. Get tar (r) sources: check

3. Install libraries that might be necessary for Mouvie Converter compilation check

4. Compile Mouvie Converter:

tar xvfz mouvie_converter_0-0-4.tar.gz check
cd mouvie_converter_0-0-4/             check 
./configure --sysconfdir=/etc 

brad@brad-desktop:~/mouvie_converter_0-0-4$ ./configure -sysconfdir=/etc
bash: ./configure: No such file or directory

Mouvie Converter runs from a Install.sh file. I tried ./configue.sh but still got the same error. 

make


Any help would appreciated.





brad@brad-desktop:~/mouvie_converter_0-0-4$ .configure.sh -sysconfdir=/etc
bash: .configure.sh: command not found

---

### Post by lisati on 2009-09-16
<never mind>

---

### Post by mc4man on 2009-09-16
Nothing to configure or build, just cd to your extracted source and at the prompt
```
 chmod +x ./install.sh
```

```
./install.sh
```

run deps
 lsdvd mencoder ffmpeg mediainfo

( mediainfo - the cli version and libs (install all 4 for gui ver. also

[http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)

---

### Post by onespeedbiker on 2009-09-16
> **mc4man said:**
> Nothing to configure or build, just cd to your extracted source and at the prompt
```
 chmod +x ./install.sh
``````
./install.sh
```run deps
 lsdvd mencoder ffmpeg mediainfo

( mediainfo - the cli version and libs (install all 4 for gui ver. also

[http://mediainfo.sourceforge.net/en/Download/Ubuntu](http://mediainfo.sourceforge.net/en/Download/Ubuntu)
I am not trying to load and run Mouvie Converter, I am trying to use checkinstall to change the tar to a deb. Can you help me here?

---

### Post by oldfred on 2009-09-16
[B]HOW TO: Using checkinstall to make .debs from sources
[/B][http://ubuntuforums.org/showthread.php?t=2356It](http://ubuntuforums.org/showthread.php?t=2356It)

 looks like your are just missing the last command:let that finish, then, instead of doing a 'make install' do this:

   ~/path/to/folder:$ sudo checkinstall

---

### Post by onespeedbiker on 2009-09-16
> **oldfred said:**
> [B]HOW TO: Using checkinstall to make .debs from sources
[/B][http://ubuntuforums.org/showthread.php?t=2356It](http://ubuntuforums.org/showthread.php?t=2356It)

 looks like your are just missing the last command:let that finish, then, instead of doing a 'make install' do this:

   ~/path/to/folder:$ sudo checkinstall Okay, I figured it out, checkinstall relies on a file in many tarballs called "configure". Unfortunately, the Mouvie Converter does not contain that file and will not work. Anyone know another way to convert a tar.gz to a deb package?

---

### Post by orlox on 2009-09-16
Mouvie Converter is just a set of nautilus scripts. As far as I know, checkinstall is used to manage installation (and deb package generation) of programs that are compiled from source, and mouvie converter doesn't fall in this category, cause it's not compiled and it's installed locally for each user in your system.

Generating a deb for this thing wouldnt be so simple.

---

### Post by fanglinyong on 2009-09-16
i think you want to install the software, you should not use sudo checkinstall ,if not ,you should use only```
checkinstall
```,by this way, you can make deb packages!

---

### Post by onespeedbiker on 2009-09-17
> **fanglinyong said:**
> i think you want to install the software, you should not use sudo checkinstall ,if not ,you should use only```
checkinstall
```,by this way, you can make deb packages!No I wanted to "use" the software to make a Debian file, but it will not work.  Thanks everyone for the help..

---

