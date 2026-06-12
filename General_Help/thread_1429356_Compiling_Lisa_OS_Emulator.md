---
title: "Compiling Lisa OS Emulator"
date: 2010-03-14
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2010-03-14
I want to run some software in the LisaEM Lisa OS emulator, and am having trouble understanding how to compile it, I have posted the text in the readme file describing how to compile in Linux:



Compiling for Linux:

You will need netpbm as well as wxWidgets 2.8.4 installed.

You will want to install/compile wxWidgets without the
shared library option.      

After installing/compiling wxWidgets, ensure that wx-config
is in your path, cd to the source code directly and run

    ./build.sh clean build
    ./build.sh install  


This will install the lisaem and lisafsh-tool binaries to
/usr/local/bin, and will install sound files to 
/usr/local/share/LisaEm/

If your system has the upx command available, it will
also compress the resulting binary with upx in order to save
space.



I'm not sure what "ensure that wx-config
is in your path" is supposed to mean, and when searching for wxWidgets in Synaptic, theres so many packages, I don't which one to install.  The website for the emulator is linked to in the first post in the E-Maculation thread: [http://www.emaculation.com/forum/viewtopic.php?t=6203](http://www.emaculation.com/forum/viewtopic.php?t=6203)

TIA

---

### Post by gmargo on 2010-03-14
wx-config is a tricky one; it is provided by at least two packages.  You will need to install one or both of these packages (just install both):
```

libwxbase2.8-dev - wxBase library (development) - non-GUI support classes of wxWidgets toolkit
libwxgtk2.8-dev - wxWidgets Cross-platform C++ GUI toolkit (GTK+ development)

```

---

### Post by ..::| Dave89 |::.. on 2010-03-15
I got this when attempting to compile:

```
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnVideoDoubleY(wxCommandEvent&)’:
lisaem_wx.cpp:1567: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1567: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnVideo2X3Y(wxCommandEvent&)’:
lisaem_wx.cpp:1598: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1598: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnSkinsOn(wxCommandEvent&)’:
lisaem_wx.cpp:1612: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1612: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘virtual bool LisaEmApp::OnInit()’:
lisaem_wx.cpp:1750: error: invalid conversion from ‘const char*’ to ‘char*’
lisaem_wx.cpp: At global scope:
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In function ‘void handle_powerbutton()’:
lisaem_wx.cpp:3774: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:3784: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:3788: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:3814: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In function ‘void lisa_powered_off()’:
lisaem_wx.cpp:3854: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In function ‘void lisa_rebooted()’:
lisaem_wx.cpp:3863: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnTraceLog(wxCommandEvent&)’:
lisaem_wx.cpp:4242: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnKEY_RESET(wxCommandEvent&)’:
lisaem_wx.cpp:4270: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:4270: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnProFilePowerX(int)’:
lisaem_wx.cpp:4530: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:4530: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnProFilePwrOffAll(wxCommandEvent&)’:
lisaem_wx.cpp:4555: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:4555: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnNewProFile(wxCommandEvent&)’:
lisaem_wx.cpp:4579: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnxNewFLOPPY()’:
lisaem_wx.cpp:4700: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In function ‘int initialize_all_subsystems()’:
lisaem_wx.cpp:5568: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5571: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5608: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5612: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5616: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5620: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5656: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5689: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5723: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5726: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5729: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5732: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5741: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5741: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5751: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5751: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5762: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5762: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5775: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5827: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5837: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5882: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5889: warning: deprecated conversion from string constant to ‘char*’
dave89@dave89-desktop:~/Desktop/lisaem-1.2.6$ 

```And this when attempting to install:

```
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
../include/../resources/lisa2icon.xpm:4551: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnVideoDoubleY(wxCommandEvent&)’:
lisaem_wx.cpp:1567: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1567: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnVideo2X3Y(wxCommandEvent&)’:
lisaem_wx.cpp:1598: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1598: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnSkinsOn(wxCommandEvent&)’:
lisaem_wx.cpp:1612: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1612: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘virtual bool LisaEmApp::OnInit()’:
lisaem_wx.cpp:1750: error: invalid conversion from ‘const char*’ to ‘char*’
lisaem_wx.cpp: At global scope:
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1866: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:1872: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In function ‘void handle_powerbutton()’:
lisaem_wx.cpp:3774: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:3784: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:3788: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:3814: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In function ‘void lisa_powered_off()’:
lisaem_wx.cpp:3854: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In function ‘void lisa_rebooted()’:
lisaem_wx.cpp:3863: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnTraceLog(wxCommandEvent&)’:
lisaem_wx.cpp:4242: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnKEY_RESET(wxCommandEvent&)’:
lisaem_wx.cpp:4270: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:4270: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnProFilePowerX(int)’:
lisaem_wx.cpp:4530: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:4530: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnProFilePwrOffAll(wxCommandEvent&)’:
lisaem_wx.cpp:4555: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:4555: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnNewProFile(wxCommandEvent&)’:
lisaem_wx.cpp:4579: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In member function ‘void LisaEmFrame::OnxNewFLOPPY()’:
lisaem_wx.cpp:4700: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp: In function ‘int initialize_all_subsystems()’:
lisaem_wx.cpp:5568: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5571: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5608: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5612: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5616: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5620: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5656: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5689: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5723: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5726: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5729: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5732: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5741: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5741: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5751: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5751: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5762: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5762: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5775: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5827: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5837: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5882: warning: deprecated conversion from string constant to ‘char*’
lisaem_wx.cpp:5889: warning: deprecated conversion from string constant to ‘char*’
dave89@dave89-desktop:~/Desktop/lisaem-1.2.6$ 
```I don't understand any of it

---

### Post by mixmaster on 2010-03-15
You can safely ignore the deprecated conversion warning.  Basically it says
that you are addressing constant data in a way which would potentially enable you to modify it.  Since modifying a constant is generally a very bad idea the compiler warns you that you might be doing something daft.  Older compilers did not produce this warning so if you compile old code on a new machine you can get swamped by it.

You can suppress it by changing the compiler warning level in the makefile, or just ignore it.

---

### Post by ..::| Dave89 |::.. on 2010-03-18
Sorry it took so long for me to reply.

Does this mean that I'm compiling it correctly, if so, it doesn't install as far as I can tell.

---

### Post by robson22 on 2012-02-15
Welcome.
I use Ubuntu 11.04.
I download lisaem-1.2.6, unpacking, install the libwxbase2.8-dev and libwxgtk2.8-dev. 
Then i start the build.sh clean build, everything is ok but in bin directory is only "lisadiskinfo" and "lisafsh-tool" binary.
Next i run sudo build.sh install, and again everything seems be ok.
In the "README" file is```
	./build.sh clean build
	./build.sh install  


This will install the lisaem and lisafsh-tool binaries to
/usr/local/bin, and will install sound files to 
/usr/local/share/LisaEm/
```

but i check and there is no the "lisaem" and "lisafsh-tool"
and folder /usr/local/share/LisaEm/ not exist

Please help me

I greet.

---

