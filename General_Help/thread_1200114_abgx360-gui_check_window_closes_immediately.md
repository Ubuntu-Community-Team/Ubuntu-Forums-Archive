---
title: "abgx360-gui check window closes immediately"
date: 2009-06-29
forum: General Help
---

### Post by nonzer0 on 2009-06-29
I installed abgx360gui-1.0.1 in ubuntu jaunty. I got the program to execute, I select the .iso, and when I click 'Launch' a window flashes real quick.

I tried installing it according to one website, then another. I just tried installing it again by following the readme.
The way I set it up is I unzipped the file. In terminal I ran ./configure, then make.

Does anyone know how to solve this. I've been trying to figure this out for 3 days.

Any help or guidance is greatly appreciated.

---

### Post by nonzer0 on 2009-06-29
This is where I got the origional instructions
[http://www.ubuntugeek.com/stealth-checking-xbox-360-games-with-abgx360-and-nautilus.html](http://www.ubuntugeek.com/stealth-checking-xbox-360-games-with-abgx360-and-nautilus.html)

---

### Post by nonzer0 on 2009-06-30
Does anyone have any info on abgx 360?

---

### Post by Darknyte on 2009-07-06
Dude I had the same problem but I tried this and it worked for me. I got it off the same link you posted up above from Ubuntu Geek. It seemed he forgot to mention that I needed libwxgtk in order to get it working.

" siggismallz says:
June 25, 2009 at 2:35 pm

to install gui version:
sudo apt-get install libwxgtk*
wget [http://abgx360.x-scene.com/abgx360gui-1.0.1.tar.gz](http://abgx360.x-scene.com/abgx360gui-1.0.1.tar.gz)
tar -zxvf abgx360gui-1.0.1.tar.gz
cd abgx360gui-1.0.1
./configure && make
to start the gui type:
./abgx360gui "

---

### Post by iceman2048 on 2009-10-14
I apologise for bumping an old thread but I have the same problem as the OP. I'm quite inexperienced with Ubuntu (and GNU/Linux in general) and would appreciate any help.

I'm running 32 bit version of Jaunty, and followed Darknyte's instructions for installing the GUI version of it. The same problem as the OP occurs, so I tried to do what I can to remedy the situation.

I started off with the README file. Quite useless, has only a solution for someone who encounters a wxWidgets not being found.

The next thing I tried was disabling compiz and trying out metacity, no dice. 

Then I tried recompiling the app according to Darknytes instructions (quite similar/exact as the ones I used to install it the first time). Here is the result of that:

```


iceman@iceman-desktop:~/abgx360gui-1.0.1$ ./configure && make
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking for ANSI C header files... (cached) yes
checking for memset... yes
checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 2.5.0... yes (version 2.8.9)
checking for wxWidgets static library... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-am
make[1]: Entering directory `/home/iceman/abgx360gui-1.0.1'
make[1]: Leaving directory `/home/iceman/abgx360gui-1.0.1'


```The first time I did it, it couldn't find 'gawk' so I used synaptic to install it. I also installed the build-essential package. 

Any help would be greatly appreciated. Thanks in advance.

---

### Post by luisfra on 2009-10-16
ok i having a error when trying to install this..

configure: error: "zlib not found!"

but i did install zlib and if i go to synaptic package manager it show has intalled it has the green box and it say zlib1g, is this the one i need or is it a diferent one

---

### Post by iceman2048 on 2009-10-25
Bump, I still havent managed to get ti workin, unfortunately. I have tried deleting the install folder in Home, then redownloading and recompiling but the same effect occurs.

to luisfra:

I have zlib1g installed with no detrimental effects (green box was there after trying to install abgx360gui). If I were you, I would try installing that. However, I'm definitely not an expert when it comes to anything linux-related.....

EDIT: luisfra

Try installing these packages:

libcurl3
libcurl3-gnutls
libcurl4-gnutls-dev
liblua5.1-curl-dev

I found that list in another blog post comment, I tried compiling the non gui version of abgx360 and it asked for libcurl. Installing these packages, and it stopped asking for libcurl. Hope that helps.

---

### Post by Rasheeke on 2009-11-03
You guys got abgx360gui to even install?  I got the newest wxWidgets (2.9) installed just fine but when I try to run 'make' for abgx360gui all I get is 

```

/usr/local/include/wx-2.9/wx/event.h: In member function &#8216;void PrettyButton::onMouseUp(wxMouseEvent&)&#8217;:
/usr/local/include/wx-2.9/wx/event.h:2872: error: &#8216;virtual bool wxEvtHandler::ProcessEvent(wxEvent&)&#8217; is inaccessible
src/abgx360gui.cpp:175: error: within this context
src/abgx360gui.cpp: In member function &#8216;void abgx360gui::CreateGUIControls()&#8217;:
src/abgx360gui.cpp:684: error: &#8216;wxSAVE&#8217; was not declared in this scope
src/abgx360gui.cpp:723: error: &#8216;wxOPEN&#8217; was not declared in this scope
src/abgx360gui.cpp:723: error: &#8216;wxFILE_MUST_EXIST&#8217; was not declared in this scope
src/abgx360gui.cpp:723: error: &#8216;wxMULTIPLE&#8217; was not declared in this scope
src/abgx360gui.cpp:725: error: &#8216;wxOVERWRITE_PROMPT&#8217; was not declared in this scope
src/abgx360gui.cpp: In member function &#8216;void abgx360gui::MnuDeleteSettingsClick(wxCommandEvent&)&#8217;:
src/abgx360gui.cpp:1047: warning: &#8216;size_t wxGetMultipleChoices(wxArrayInt&, const wxString&, const wxString&, const wxArrayString&, wxWindow*, int, int, bool, int, int)&#8217; is deprecated (declared at /usr/local/include/wx-2.9/wx/generic/choicdgg.h:335)
src/abgx360gui.cpp: In member function &#8216;void abgx360gui::MyRegionButtonClick(wxCommandEvent&)&#8217;:
src/abgx360gui.cpp:2036: warning: &#8216;size_t wxGetMultipleChoices(wxArrayInt&, const wxString&, const wxString&, const wxArrayString&, wxWindow*, int, int, bool, int, int)&#8217; is deprecated (declared at /usr/local/include/wx-2.9/wx/generic/choicdgg.h:335)
src/abgx360gui.cpp: In member function &#8216;void abgx360gui::MatchOnlyButtonClick(wxCommandEvent&)&#8217;:
src/abgx360gui.cpp:2083: warning: &#8216;size_t wxGetMultipleChoices(wxArrayInt&, const wxString&, const wxString&, const wxArrayString&, wxWindow*, int, int, bool, int, int)&#8217; is deprecated (declared at /usr/local/include/wx-2.9/wx/generic/choicdgg.h:335)
make[1]: *** [abgx360gui-abgx360gui.o] Error 1
```

...so anybody know what's wrong with that or should I make a new thread with this?

---

### Post by iceman2048 on 2009-11-22
This is the second time I'm bumping a relatively old thread:) Apologies. 

I don't know how to fix any of the specific problems in this thread but I did manage to get ABGX360GUI running on Ubuntu 9.04. Basically, I installed the CLI version first (ABGX360) then tried installing ABGX360GUI using Darknyte's instructions and it worked! I just downloaded the command line version, extracted it, used the terminal to cd into that folder, then executed ./configure && make. 

Then I downloaded the gui version, extracted it, used terminal to cd into it, then ran ./configure && make. To start the program I used ./abgx360gui.

If it matters, I had extracted the packages to my home folder, then created a launcher that I put in my top panel.

Hope that helps!

---

### Post by r3dO on 2009-12-02
> **luisfra said:**
> ok i having a error when trying to install this..

configure: error: "zlib not found!"

but i did install zlib and if i go to synaptic package manager it show has intalled it has the green box and it say zlib1g, is this the one i need or is it a diferent one


hi, in the README file i have found this:

[FONT="Courier New"]abgx360 requires libcurl ([http://curl.haxx.se/download.html](http://curl.haxx.se/download.html)) and zlib ([http://www.zlib.net/](http://www.zlib.net/))

To install them on systems with apt-get:
sudo apt-get install libcurl4-openssl-dev zlib1g-dev[/FONT]

try, it was good for me ;)

---

### Post by false_chicken on 2011-03-17
I know this is old but I have the solution. 

To compile and install abgx360:
./configure
make
sudo make install

Do that for both abgx360 and the Gui. Then run by doing: abgx360gui

---

