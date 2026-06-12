---
title: "having a hard time with terminal"
date: 2010-09-23
forum: General Help
---

### Post by cadcam on 2010-09-23
so i'm trying to see what version of kompozer i have on my computer.  I'm having trouble viewing a remote site, and my version doesn't look like the screen shots .8a4.  so, i typed dpgk -l to see what i have on my computer.  the list is big, and when i scroll up, it only gets to the l's before it stops going up.  is this some sort of short memory thing for terminal?  how can i view the entire list?  

whats the correct terminal command to check the version of a program?

thanks,
A

---

### Post by qamelian on 2010-09-23
Try: 
```
apt-cache policy app_name
```

---

### Post by cadcam on 2010-09-23
thanks.  that worked.  indeed, it was an older version.  after following the instructions to add a new software source on kompozer's website, i installed the latest (b3).  

HOWEVER, now it won't open.  i open it in terminal, and it just does nothing.  it acts like it executed a command and is ready to receive another.  

please help?

---

### Post by alphacrucis2 on 2010-09-23
> **cadcam said:**
> thanks.  that worked.  indeed, it was an older version.  after following the instructions to add a new software source on kompozer's website, i installed the latest (b3).  

HOWEVER, now it won't open.  i open it in terminal, and it just does nothing.  it acts like it executed a command and is ready to receive another.  

please help?

Try installing it using a PPA. See:

[https://launchpad.net/~giuseppe-iuculano/+archive/ppa]("https://launchpad.net/~giuseppe-iuculano/+archive/ppa")


Forget this. I get the same problem as you when installing it from the PPA. Hmmm. The program exits with no error message

---

### Post by cadcam on 2010-09-23
i did that.  i installed it by manually pasting the software sources in.  when i did the sudo add ppa thing in terminal, it said it was unchanged, so i assume the software sources did it.  

mantra@Mantra:~$ apt-cache policy kompozer
kompozer:
  Installed: 1:0.8~b3-2~ubuntu10.04~1
  Candidate: 1:0.8~b3-2~ubuntu10.04~1
  Version table:
 *** 1:0.8~b3-2~ubuntu10.04~1 0
        500 [http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/](http://ppa.launchpad.net/giuseppe-iuculano/ppa/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
     1:0.8~b1-2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Packages
mantra@Mantra:~$

according to my computer, its installed, but I seem unable to use it....and by that I mean open it.  

thanks a lot for the help, please suggest something else.

thanks,
A

---

### Post by alphacrucis2 on 2010-09-23
I purged the PPA and it reverted to the version from the Lucid repos which appears to be 08b1. This version starts up ok. Not sure why the b3 version doesn't work.

---

### Post by cadcam on 2010-09-23
allright.  well i can download the .tar.gz file from the dev site.  

would you please tell me how I would go about installing the tar.gz file?

the ./configure command says no such file or directory after i extract it.  am I supposed to do something else with this?

every time i try to build from source, i get all these expected " ' before something" errors

thanks,
A

---

### Post by alphacrucis2 on 2010-09-23
I found a post on the Geckozone (French) forums where someone was having the same problem with Kompozer on Linux Mint. My French isn't very good but from what I can understand, they also had to revert to 08b1. I haven't found much else on google.

---

### Post by CharlesA on 2010-09-23
> **cadcam said:**
> allright.  well i can download the .tar.gz file from the dev site.  

would you please tell me how I would go about installing the tar.gz file?

the ./configure command says no such file or directory after i extract it.  am I supposed to do something else with this?

thanks,
A

You would have to extract it, since normally a tar.gz file is the source code, then run the **make** command.

You'd need to have a compiler installed as well.

Give it a shot, but if it doesn't work, you probably have to install build-essential: ```
sudo apt-get install build-essential
```

Also check [here]("https://help.ubuntu.com/community/CompilingSoftware").

---

### Post by cadcam on 2010-09-23
yeah, my thought was the same, but i can't make the contents of the tarball....  ( i have all the recommended compiling packages installed)

mantra@Mantra:~/Downloads$ cd kompozer/
mantra@Mantra:~/Downloads/kompozer$ dir
bloaturls.txt        kompozer-config    libplds4.so           plugins
chrome            libfreebl3.chk     libsmime3.so           regxpcom
components        libfreebl3.so      libsoftokn3.chk           res
defaults        libgfxpsshar.so    libsoftokn3.so           run-mozilla.sh
dependentlibs.list  libgkgfx.so        libssl3.so           shlibsign
dictionaries        libgtkembedmoz.so  libxpcom_compat.so      TestGtkEmbed
elf-dynstr-gc        libgtkxtbin.so     libxpcom_core.so        updater
extensions        libjsj.so           libxpcom.so           updates
greprefs        libmozjs.so        libxpistub.so           xpcshell
icons            libnspr4.so        LICENSE               xpicleanup
install.log        libnss3.so           mangle               xpidl
kompozer        libnssckbi.so      mozilla-xremote-client  xpt_dump
kompozer-bin        libplc4.so           nsinstall           xpt_link
mantra@Mantra:~/Downloads/kompozer$ make
make: *** No targets specified and no makefile found.  Stop.


i'm a little confused on the run-mozilla.sh  ?  is this something i should be doing something with?

thanks,
A

---

### Post by cadcam on 2010-09-23
at alphacrucis , thanks for checking that out, and your dredging of the french forums ;)

---

### Post by alphacrucis2 on 2010-09-24
Looks like the archive you downloaded might have been the binaries. They link two archives on this site:

[http://kazhack.org/?post/2010/03/02/KompoZer-0.8b3]("http://kazhack.org/?post/2010/03/02/KompoZer-0.8b3")

The one with i686 in the name is the binaries. You would want the source tarball one to compile from source. To test out the binary version, extract to home, it will create a folder called kompozer under your home dir. Then start up a terminal and type:

```
cd kompozer
./kompozer
```

Worked ok for me. V 08b3. I've no idea why the packaged one doesn't work.

---

### Post by cadcam on 2010-09-24
huh, ok, well, i just ran the kompozer file in that tarball through term and it worked......then i threw it in the app menu and created a launcher and its all good.

thanks man :)

now, if i can only figure out HOW IN THE HECK to get kompozer to give me a remote view of the site, instead of a local view. 


WAIT< NEVERMIND, its still the old version......

i need .8a4, but i'll give this another try....hrmmmmm  there is no remote view in .8a3

[http://www.open4g.com/index.php?option=com_content&view=article&id=139:kompozer-08a4-released&catid=1:latest&Itemid=2](http://www.open4g.com/index.php?option=com_content&view=article&id=139:kompozer-08a4-released&catid=1:latest&Itemid=2)

thanks,
A

---

### Post by alphacrucis2 on 2010-09-24
> **cadcam said:**
> huh, ok, well, i just ran the kompozer file in that tarball through term and it worked......then i threw it in the app menu and created a launcher and its all good.

thanks man :)

now, if i can only figure out HOW IN THE HECK to get kompozer to give me a remote view of the site, instead of a local view. 

thanks,
A

I don't think it offers a "remote" view. You would probably have to use an actual web browser for that. If you just mean see and manage the files on the web server then it does have a site manager but I've never used that feature. I use filezilla for that.

---

### Post by cadcam on 2010-09-24
naw i was looking for this....  that remote tab isn't on previous versions.  i'm coming from dreamweaver, but I'm tired of the adobe's money mongering, so I'm going open source for my future comp work.  but coming from dreamweaver, i'm kind of bred to have a local and remote explorer option that can be easily synched.  i freak out without it.

[IMG]http://kazhack.org/public/kpz-08a4-sm.png[/IMG]

---

### Post by cadcam on 2010-09-24
AND I"M THERE.  sweeeet.  runing alpha 4, and its all good, at least now until i enter my site settings and watch the world crash on me....but its good till then.

thanks a lot alphacrucis2

---

### Post by alphacrucis2 on 2010-09-24
> **cadcam said:**
> naw i was looking for this....  that remote tab isn't on previous versions.  i'm coming from dreamweaver, but I'm tired of the adobe's money mongering, so I'm going open source for my future comp work.  but coming from dreamweaver, i'm kind of bred to have a local and remote explorer option that can be easily synched.  i freak out without it.

[IMG]http://kazhack.org/public/kpz-08a4-sm.png[/IMG]

Ok. I didn't know 08b4 was available. Filezilla gives a local and remote pane for moving files to & from an ftp or sftp site. Not so convenient as it is a separate program.

---

