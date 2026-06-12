---
title: "How to successfully install Ettercap 0.7.4(.1)"
date: 2012-03-19
forum: General Help
---

### Post by PalqkA on 2012-03-19
Hello everyone.

I am a beginner and I wanted to get newest version of Ettercap and use it.
I met some problems during installing it and at last I made it work.
So I wanted to show the other people how to do this with success.

In my work I used a lot of threads and finally 1 helped me, so I`ll share it with you.

The original post is in Spanish here > [https://sites.google.com/site/websiteselblogdelhacker/instal-lar-ettercap-ng-0-7-4](https://sites.google.com/site/websiteselblogdelhacker/instal-lar-ettercap-ng-0-7-4)
This guide worked for me on Ubuntu 11.10 and  Ettercap 0.7.4.1 [ettercap.sourceforge.net/index.php]("http://ubuntuforums.org/ettercap.sourceforge.net/index.php")

So here we go.

Firstly for sure you have to download Ettercap from [http://ettercap.sourceforge.net/download.php](http://ettercap.sourceforge.net/download.php)

after you download it and extract it, you will need to get into terminal and install a lot of stuffs to get ettercap fully functional.

Here is what you will need :

**Part 1.**

sudo apt-get install build-essential 
sudo apt-get install linux-headers-`uname -r`

**Part 2. Installing the Libraries**

sudo apt-get install libpcre3-dev 
sudo apt-get install libpcap0.8-dev 
sudo apt-get install libnet1-dev 
sudo apt-get install openssl
sudo apt-get install libssl-dev 
sudo apt-get install ncurses-bin 
sudo apt-get install libncurses5-dev 
sudo apt-get install libnet6-1.3-dev 
sudo apt-get install libpthread-stubs0-dev 
sudo apt-get install zlib1g-dev 
sudo apt-get install libltdl-dev 
sudo apt-get install pango-graphite
sudo apt-get install pkg-config 
sudo apt-get install libpango1.0-dev 
sudo apt-get install libatk1.0-dev 
sudo apt-get install libgtk2.0-dev 

**Part 3. Extras**

sudo apt-get install autoconf
sudo apt-get install byacc

**Part 4. The patch**

[https://docs.google.com/file/d/0B5pFBZbg6J5HNDU4NjAzMmEtZWE0NS00ZWQzLWIzZWQtZWU1ODNmZmE0Mjdl/edit](https://docs.google.com/file/d/0B5pFBZbg6J5HNDU4NjAzMmEtZWE0NS00ZWQzLWIzZWQtZWU1ODNmZmE0Mjdl/edit)

(to download when you open the page go to up left corner, click on File and then Download.)

I downloaded it into ettercap main dir. So if you haven't - you should now copy the patch file in the ettercap main directory.

**Part 5. Apply the patch**

My ettercap folder is/was on my Desktop so when I opened a terminal I navigate to my desktop. 
Get into ettercap folder.

Type in terminal:

patch -p1 < ettercap-0.7.4-autotools.patch

**Part 6.**

After the patching is done type we can continue with this:

./autogen.sh

In the terminal window you should see something like this:

libtoolize: copying file `libltdl/lt_dlloader.c'
libtoolize: copying file `libltdl/lt_error.c'
libtoolize: copying file `libltdl/ltdl.c'
libtoolize: copying file `libltdl/ltdl.h'
libtoolize: copying file `libltdl/slist.c'
libtoolize: Remember to add `LT_CONFIG_LTDL_DIR([libltdl])' to `configure.in'.
libtoolize: Consider using `AC_CONFIG_AUX_DIR([libltdl/config])' in configure.in.
libtoolize: Consider using `AC_CONFIG_MACRO_DIR([libltdl/m4])' in configure.in.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
running aclocal
running autoheader
running autoconf
running automake


**Part 7. Configure**

In the guide it was shown this:

./configure --enable-plugins --enable-debug

I used this:

./configure --enable-plugins --enable-debug --enable-gtk

With these settings the install dir will be : /usr/local

When the configuration is done you will see this or something like this :

Libraries : 

LIBPCAP ................ default
LIBNET ................. default
LIBSSL ................. default
NCURSES ................ default
GTK+ ................... yes

Functionalities : 

Debug mode ............. yes
Plugin support ......... yes
Passive DNS ............ yes
Perl regex in filters .. yes
Iconv UTF-8 support .... yes

**Part 8. Fixing a line**

So this was the most important part for me. As I wanted to have GTK (graphic interface) i had a problem where the making of the install was unable to read something so i was unable to install Ettercap with GTK.

Here is the salvation.

In terminal considering you are into Ettercap main directory, type this:

cd src/
sudo gedit Makefile

so the text redactor will appear and you will need to find this line:

LIBS = -lresolv -lz -lpthread -lltdl -ldl -ldl

using the search function for example and change it with this:

LIBS = -lresolv -lz -lpthread -lltdl -ldl -ldl  -lpcap -lnet -lssl  -lcrypto -lpcre -lpanel -lmenu -lform -lncurses -pthread -lgtk-x11-2.0  -lgdk-x11-2.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0  -lcairo -lfreetype -lfontconfig -lpango-1.0 -lgmodule-2.0 -latk-1.0  -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0   -lgthread-2.0 

and then save the file.

**NOTE:** you can use your favorite text redactor for sure but the point here is using the sudo command to open it because the Makefile is locked for non-sudo usage.
 
**Part 9. The ef_syntax.c file**

If by some reasons you are missing "ef_syntax.c" file into "utils/etterfilter/" you can download it from here : [https://docs.google.com/file/d/0B5pFBZbg6J5HNjU1ZGU4NzAtZWM4ZC00YTI1LWEzODAtOGNiNTY1MTk0NzYw/edit](https://docs.google.com/file/d/0B5pFBZbg6J5HNjU1ZGU4NzAtZWM4ZC00YTI1LWEzODAtOGNiNTY1MTk0NzYw/edit)
and put it in the place.

**Part 10. "make" and "make install"**

Now in terminal navigate to the Ettercap directory and type following commands:

make

If you don't get any errors till the end of "making" (as it should be), type the next command into the terminal:

sudo make install

after finishing you should have working Ettercap with GTK!

type in terminal: sudo ettercap -G

-------------------------------------------------------------------------------------------------------

All the information above is taken and translated (as much as my English can do it ;)) from the following site : [https://sites.google.com/site/websiteselblogdelhacker/instal-lar-ettercap-ng-0-7-4](https://sites.google.com/site/websiteselblogdelhacker/instal-lar-ettercap-ng-0-7-4) !!! I don't have any credits with the doing of the guide but translating it and saying what have I done.

Would be nice to know I helped someone.

Wish you luck.

---

### Post by davywavy on 2012-03-24
Hello PalqkA

I am following your instructions.  I have extracted ** Ettercap 0.7.4(.1) **to my desktop.  I did **sudo apt-get install build-essential **OK but when I tried **sudo apt-get install linux-headers-`uname -r`** I got the message** E: Unable to locate package linux-headers-uname-r**.
Am I typing the correct command?
I have recently switched to linux from MS windows and am not an expert.
I want to get this step sorted and carry on through your instructions in the correct order.

I hope you can help.

---

### Post by PalqkA on 2012-03-25
These lines are to ensure, that you are on most recent version of your Ubuntu.
You can skip it if you have all updates done.

Anyway what OS are you using?

---

### Post by davywavy on 2012-03-25
I'm using version 11.10 but have only just installed it. I did use Puppy linux a bit from a live disk but when I removed XP from my laptop's hard drive I thought I would try Ubuntu.
I will check all updates are installed and try again.

---

### Post by PalqkA on 2012-03-25
Sure thing :) this command worked on my laptop with the same version of Ubuntu :)
I just tried the command again and it didn't gave me any error. I hope you type it correct. you can copy/paste it:

sudo apt-get install linux-headers-`uname -r`

---

### Post by davywavy on 2012-03-25
Hello again

I managed to install **uname -r** and everything else and followed the instructions in order but when I entered **ettercap -G** I got the message

**GTK support not compiled in ettercap**

I can start it in text mode but would like the GUI to work.  Any ideas where I have gone wrong?

---

### Post by PalqkA on 2012-03-26
Here is your answer.
So, to compile it with -G option you should have installed all the things I posted and after you are in ettercap folder and type 
 ./configure --enable-plugins --enable-debug --enable-gtk in terminal you should have a lot of lines moving up and when they finish you should see GTK+ ...... yes in lib line. if you don't see this line - you have something wrong. Re-read the guide and if you don'd understand something or you think something is wrong - throw a message here. I`ll try to answer you as soon as possible.

P.S.

The main reason from me not having a "-G" were the place you add a libraries in part 8. You should find the exact line and replace with the exact line I posted in the guide.
 If you still have a problems after all you can pm me and i`ll give you skype to see what are you misdoing.
[B]

Part 7. Configure[/B]

In the guide it was shown this:

./configure --enable-plugins --enable-debug

I used this:

./configure --enable-plugins --enable-debug --enable-gtk

With these settings the install dir will be : /usr/local

When the configuration is done you will see this or something like this :

Libraries : 

LIBPCAP ................ default
LIBNET ................. default
LIBSSL ................. default
NCURSES ................ default
GTK+ ................... yes

Functionalities : 

Debug mode ............. yes
Plugin support ......... yes
Passive DNS ............ yes
Perl regex in filters .. yes
Iconv UTF-8 support .... yes

---

### Post by davywavy on 2012-03-26
Hello

I got all readings identical to yours, including** GTK+........yes**. But still got the problem mentioned.
Any thoughts?

---

### Post by PalqkA on 2012-03-30
the only thing i can advise you is to go to your ettercap folder trough terminal window and write following lines:
sudo make uninstall
make clean
make
sudo make install

I hope this will works for you.
Sorry for late response but I wasn't be able to do it earlier.

---

### Post by davywavy on 2012-03-31
I have followed your latest instructions. Typing in **ettercap -G **now brings up the GUI window but there are no menu options to actually use it.  Do you know why this might be?

---

### Post by PalqkA on 2012-03-31
As you probably haven't noticed  - the menus are shown on the up part of the screen :) like it is maximized :) this is from Unity graphics :) 
If you haven't understand me when you open your window of ettercap and he is in front of all other windows put your mouse on the top part of your screen and you will see the menus :) (where your clock date wireless etc buttons are shown but not over them ... in the middle for example :) or just maximize your window of ettercap ;))

---

### Post by davywavy on 2012-03-31
Thanks
I'm getting there slowly.  The menu options were where you suggested but when I go to **UNIFIED SNIFFING** there are no interfaces listed and if I type in wlan0 I get the response **INVALID INTERFACE**.
Do you know why ettercap is not displaying wlan0 in GTK?  It picks up wlan0 in text mode.

---

### Post by PalqkA on 2012-04-01
sudo ettercap -G

---

### Post by davywavy on 2012-04-01
Thanks again.

I now have an operable GUI.
However, when I set my router as target 1 and a second PC as target 2,  ARP poison (remote) then start sniffing,  I get no results whatever I do or log into on the target PC.
Are there settings I need to make in the GUI at some point to make it work?

Thanks for your help and patience so far.  I's much appreciated.

---

### Post by PalqkA on 2012-04-01
Usually ettercap by himself can't log from sites with SSL. Take a look on some youtube videos for example so you will get some information about usage and possible combinations :)
No problems. I help if i can. Wish you luck!

---

### Post by davywavy on 2012-04-03
Hello PalqkA

Following the instructions on a site by  a blogger called JKOOK, I used ettercap in text mode along with arpspoof and SSLstrip and successfully sniffed other devices on my wlan.

I have discovered that since then, ettercap 0.7.4 works on it's own in GUI mode.

I now feel I can monitor my network better to keep it and it's users safe.

Thanks once again for all your help.

---

### Post by joekeyel on 2012-04-14
Hail PalqkA,

I have problem after run the command make, sudo make install...

the error after make install command are

ration
collect2: ld returned 1 exit status
make[2]: *** [ettercap] Error 1
make[2]: Leaving directory `/home/joe/Downloads/ettercap/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/joe/Downloads/ettercap/src'
make: *** [all-recursive] Error 1


before this i get this value


LIBPCAP ................ default
LIBNET ................. default
LIBSSL ................. default
NCURSES ................ default
GTK+ ................... yes

Functionalities : 

Debug mode ............. yes
Plugin support ......... yes
Passive DNS ............ yes
[COLOR=Red]Perl regex in filters .. NO[/COLOR]
Iconv UTF-8 support .... yes
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]    		 		 		 		 		

hope to hear from you soon

tq
	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=11794371")

---

### Post by Rakeshvijayan on 2012-04-19
> **davywavy said:**
> Thanks again.

I now have an operable GUI.
However, when I set my router as target 1 and a second PC as target 2,  ARP poison (remote) then start sniffing,  I get no results whatever I do or log into on the target PC.
Are there settings I need to make in the GUI at some point to make it work?

Thanks for your help and patience so far.  I's much appreciated.

you need to edit /etc/etter.conf file 

remove # from the following line like this ,its for sniffing password from https , I think you had tried with https sites , before editing this check with by login to your modem or router ,because it is http ..........



# if you use iptables:
   redir_command_on = "iptables -t nat -A PREROUTING -i %iface -p tcp --dport %port -j REDIRECT --to-port %rport"
   redir_command_off = "iptables -t nat -D PREROUTING -i %iface -p tcp --dport %port -j REDIRECT --to-port %rport"

[PalqkA]("http://ubuntuforums.org/member.php?u=1158220")   thanks for the tutorial ,is this guide possible to install on ubuntu 12.04.now am using the beta version of 12.04 and back track ,
if it not I need to go back on 11.10

---

### Post by Rakeshvijayan on 2012-04-21
[http://sourceforge.net/projects/ettercap/files/ettercap/0.7.4-Lazarus/](http://sourceforge.net/projects/ettercap/files/ettercap/0.7.4-Lazarus/)   



use this link to donwnload ettercap 0-7-4

---

### Post by Rakeshvijayan on 2012-04-21
[I]I  got the error message when I use the make command 


collect2: ld returned 1 exit status
make[2]: *** [ettercap] Error 1
make[2]: Leaving directory `/home/vb/Desktop/ettercap/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vb/Desktop/ettercap/src'
make: *** [all-recursive] Error 1
vb@vbn:~/Desktop/ettercap$ 



what should I do ?




//// This is the content allready there **on sudo gedit Makefile   **[/I]**EC_LIBS = -lresolv -lz -lpthread -lltdl -ldl -ldl  -lpcap -lnet -lssl -lcrypto -lpcre -lpanel -lmenu -lform -lncurses -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lfreetype -lfontconfig -lpango-1.0 -lgmodule-2.0 -latk-1.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0   -lgthread-2.0    **[I]I didnt change any thing there is this is problem ? for getting error /////////
[/I]

---

### Post by PalqkA on 2012-04-21
> **joekeyel said:**
> Hail PalqkA,

I have problem after run the command make, sudo make install...

the error after make install command are

ration
collect2: ld returned 1 exit status
make[2]: *** [ettercap] Error 1
make[2]: Leaving directory `/home/joe/Downloads/ettercap/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/joe/Downloads/ettercap/src'
make: *** [all-recursive] Error 1


before this i get this value


LIBPCAP ................ default
LIBNET ................. default
LIBSSL ................. default
NCURSES ................ default
GTK+ ................... yes

Functionalities : 

Debug mode ............. yes
Plugin support ......... yes
Passive DNS ............ yes
[COLOR=Red]Perl regex in filters .. NO[/COLOR]
Iconv UTF-8 support .... yes
                                                                                                  [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                                                

hope to hear from you soon

tq
                                                                [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=11794371")
Hello there.
I had problems with my laptop so I had no place to work from.
I assume that there are 2-3 possible problems that you can check before you try again and there they are:
1. You probably haven't added all the needed libs  from step 2(and 3).
2. You haven't applied the patch correct.
3. Your 8th step isn't correct.

Wish you luck :)

---

### Post by PalqkA on 2012-04-21
> **Rakeshvijayan said:**
> [I]I  got the error message when I use the make command 


collect2: ld returned 1 exit status
make[2]: *** [ettercap] Error 1
make[2]: Leaving directory `/home/vb/Desktop/ettercap/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vb/Desktop/ettercap/src'
make: *** [all-recursive] Error 1
vb@vbn:~/Desktop/ettercap$ 



what should I do ?




//// This is the content allready there **on sudo gedit Makefile   **[/I]**EC_LIBS = -lresolv -lz -lpthread -lltdl -ldl -ldl  -lpcap -lnet -lssl -lcrypto -lpcre -lpanel -lmenu -lform -lncurses -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo -lfreetype -lfontconfig -lpango-1.0 -lgmodule-2.0 -latk-1.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0   -lgthread-2.0    **[I]I didnt change any thing there is this is problem ? for getting error /////////
[/I]
Hello there.
Yes probably this is your problem. Read the step again and you don't need to make file but to open existing one, search for **EXACT** line and change it.
Wish you luck.

---

### Post by Rakeshvijayan on 2012-04-23
**finally I installed it ,but when I tried to use the ettercaap network interface is not unavailable message appear ,on undefined sniffing ,see the attachment  **

---

### Post by PalqkA on 2012-04-23
How about this:
**sudo ettercap -G**
you haven't read the whole thread because I already said once it should be started with sudo to have some options if you don't have them 
):P

---

### Post by Rakeshvijayan on 2012-04-24
> **PalqkA said:**
> How about this:
**sudo ettercap -G**
you haven't read the whole thread because I already said once it should be started with sudo to have some options if you don't have them 
):P
[B]
THANKS FRIEND 

[/B]*I really forgot to make sudo before that command , now *ettercap is working great on ubuntu 11.10   :guitar:

---

### Post by PalqkA on 2012-04-24
Don't worry ;)

---

### Post by Milord on 2012-04-26
After many days i finally found this guide...
everything is now working properly, specially the issues with GTK during sudo make install..](*,)
i really appreciate your job in traslating the guide from spanish and i wanna thank you so much=D>
also thanks to original writer of thus guide
i can finally start testing with ettercap 0.7.4.1 version

Using Linux Mint 12 (Lisa)

---

### Post by PalqkA on 2012-04-27
Nice to know it helped.
And also that this guide works for another platform too :popcorn:

---

### Post by nightcrawler2012 on 2012-06-12
I did everything step by step and I keep getting the same results......... but their is one step missing....................

#shutdown -r now

after I did that then 

root@unknown~/ettercap# ettercap -v

ettercap 0.7.4.1 copyright 2001-2011 ALoR & NaGA

ettercap 0.7.4.1
root@unknown~/ettercap#

---

### Post by pepangskie on 2012-07-02
> **Rakeshvijayan said:**
> **finally I installed it ,but when I tried to use the ettercaap network interface is not unavailable message appear ,on undefined sniffing ,see the attachment  **

Gud Day
We shared the same errors what u done to finally installed it?

Hope that you'll share it to me.. Thanks

---

### Post by PalqkA on 2012-07-10
> **pepangskie said:**
> Gud Day
We shared the same errors what u done to finally installed it?

Hope that you'll share it to me.. Thanks

Check other posts in this thread and you will find the answer :)

---

### Post by PalqkA on 2012-07-10
> **nightcrawler2012 said:**
> I did everything step by step and I keep getting the same results......... but their is one step missing....................

#shutdown -r now

after I did that then 

root@unknown~/ettercap# ettercap -v

ettercap 0.7.4.1 copyright 2001-2011 ALoR & NaGA

ettercap 0.7.4.1
root@unknown~/ettercap#

Looks like most of us doesn't needed this step.
Anyway I hope it would help someone.

---

### Post by konoha91 on 2012-11-19
[B]Part 7. Configure
[/B]./configure --enable-plugins --enable-debug --enable-gtk
Result:
bash: ./configure--enable-plugins--enable-debug-enable-gtk: No such file or directory
amaterasu@ubuntu:~/Desktop/ettercap/ettercap$ ./configure --enable-plugins --enable-debug --enable-gtk
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking whether make sets $(MAKE)... (cached) yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking if your compiler supports __VA_ARGS__ in macro declarations... yes
checking for bison... no
checking for byacc... byacc
checking for flex... no
checking for lex... no
configure: error: flex was not found, please install

What should i do?
Thanks in advance.

---

### Post by konoha91 on 2012-11-19
/usr/lib/gcc/i686-linux-gnu/4.7/../../../i386-linux-gnu/libgdk-x11-2.0.so: could not read symbols: Invalid operation
collect2: error: ld returned 1 exit status
make[2]: *** [ettercap] Error 1
make[2]: Leaving directory `/home/amaterasu/Desktop/ettercap/ettercap/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/amaterasu/Desktop/ettercap/ettercap/src'
make: *** [all-recursive] Error 1


HELP!!!

---

### Post by pointsss on 2012-12-09
Can anyone help me I have the following problem :

make[3]: *** [install-pkglibLTLIBRARIES] Error 126
make[3]: Leaving directory `/home/pointsss/Downloads/ettercap (2)/plug-ins/arp_cop'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/pointsss/Downloads/ettercap (2)/plug-ins/arp_cop'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/pointsss/Downloads/ettercap (2)/plug-ins'
make: *** [install-recursive] Error 1

I see it in the end of the installation and I thing it is only for the plug-ins. There is no errors in the configuring the installation.

Please help!

---

### Post by 7Starphy on 2013-02-19
Sorry for reviving this topic , but I am yet again desperate for solutions. I keep getting the following error , I did everything as said by PalqkA ,```
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libgtk-x11-2.0.so: undefined reference to symbol 'gdk_threads_enter'
/usr/bin/ld: note: 'gdk_threads_enter' is defined in DSO /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libgdk-x11-2.0.so so try adding it to the linker command line
/usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libgdk-x11-2.0.so: could not read symbols: Invalid operation
collect2: error: ld returned 1 exit status
make[2]: *** [ettercap] Error 1
make[2]: Leaving directory `/home/srinath/Desktop/ettercap/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/srinath/Desktop/ettercap/src'
make: *** [all-recursive] Error 1

```

Can anyone help me out ? I am using Ubuntu 12.10.

---

### Post by PalqkA on 2013-02-26
> **7Starphy said:**
> Sorry for reviving this topic , but I am yet again desperate for solutions. I keep getting the following error , I did everything as said by PalqkA ,```
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libgtk-x11-2.0.so: undefined reference to symbol 'gdk_threads_enter'
/usr/bin/ld: note: 'gdk_threads_enter' is defined in DSO /usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libgdk-x11-2.0.so so try adding it to the linker command line
/usr/lib/gcc/x86_64-linux-gnu/4.7/../../../x86_64-linux-gnu/libgdk-x11-2.0.so: could not read symbols: Invalid operation
collect2: error: ld returned 1 exit status
make[2]: *** [ettercap] Error 1
make[2]: Leaving directory `/home/srinath/Desktop/ettercap/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/srinath/Desktop/ettercap/src'
make: *** [all-recursive] Error 1

```Can anyone help me out ? I am using Ubuntu 12.10.

As I remember, if you can install it without GTK, then you haven't  applied the patch correctly. Otherwise you should take a look on steps :  5,6,8 and 9. mostly on step 8 I think. You have to be sure you edited the right lines or it won't work. If I'm not wrong it was the 2nd in search.
Wish you luck!

---

