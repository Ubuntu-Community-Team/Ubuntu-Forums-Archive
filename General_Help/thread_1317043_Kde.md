---
title: "Kde"
date: 2009-11-06
forum: General Help
---

### Post by quimkaos on 2009-11-06
i want have KDE also available in Ubuntu.

any hints how do it correctly?

---

### Post by Giblet5 on 2009-11-06
Install kubuntu-desktop, kde-base, and kde-admin from Synaptic.

It's one of the first things I do on any Ubuntu install.

Why limit yourself, right?


Once installed (I configure kdm BTW), you can choose the session type from the login screen.

---

### Post by undecim on 2009-11-06
in a terminal, run the command "sudo aptitude install kubuntu-desktop" to install all packages that come with Kubuntu, which includes KDE and KDE apps

---

### Post by quimkaos on 2009-11-06
> **Giblet5 said:**
> Install kubuntu-desktop, kde-base, and kde-admin from Synaptic.

It's one of the first things I do on any Ubuntu install.

Why limit yourself, right?


Once installed (I configure kdm BTW), you can choose the session type from the login screen.

a few year ago thats what i did. install linux then x then gnome and kde... but then i stopped using linux. now that i'am back i nead to re-learn most of the stuff again...

---

### Post by quimkaos on 2009-11-06
i do prefer the look of kde... but kompiz seams not to be working corectly

---

### Post by Giblet5 on 2009-11-06
What's the output of ```
xdpyinfo
```

Compiz won't work if you don't have certain acceleration capabilities (glx and composite extensions).

---

### Post by quimkaos on 2009-11-06
```

name of display:    :0.0             
version number:    11.0              
vendor string:    The X.Org Foundation
vendor release number:    10604000    
X.Org version: 1.6.4                  
maximum request size:  16777212 bytes 
motion buffer size:  256              
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst                       
number of supported pixmap formats:    7            
supported pixmap formats:                           
    depth 1, bits_per_pixel 1, scanline_pad 32      
    depth 4, bits_per_pixel 8, scanline_pad 32      
    depth 8, bits_per_pixel 8, scanline_pad 32      
    depth 15, bits_per_pixel 16, scanline_pad 32    
    depth 16, bits_per_pixel 16, scanline_pad 32    
    depth 24, bits_per_pixel 32, scanline_pad 32    
    depth 32, bits_per_pixel 32, scanline_pad 32    
keycode range:    minimum 8, maximum 255            
focus:  window 0x4800002, revert to PointerRoot     
number of extensions:    29                         
    BIG-REQUESTS                                    
    Composite                                       
    DAMAGE                                          
    DOUBLE-BUFFER                                   
    DPMS                                            
    DRI2                                            
    GLX                                             
    Generic Event Extension                         
    MIT-SCREEN-SAVER                                
    MIT-SHM                                         
    NV-CONTROL                                      
    NV-GLX                                          
    RANDR                                           
    RECORD                                          
    RENDER                                          
    SECURITY                                        
    SHAPE                                           
    SYNC                                            
    X-Resource                                      
    XC-MISC                                         
    XFIXES                                          
    XFree86-DGA                                     
    XFree86-VidModeExtension                        
    XINERAMA                                        
    XINERAMA                                        
    XInputExtension                                 
    XKEYBOARD                                       
    XTEST                                           
    XVideo                                          
default screen number:    0                         
number of screens:    1                             

screen #0:
  dimensions:    2880x900 pixels (822x263 millimeters)
  resolution:    89x87 dots per inch                  
  depths (7):    24, 1, 4, 8, 15, 16, 32              
  root window id:    0x13c                            
  depth of root window:    24 planes                  
  number of colormaps:    minimum 1, maximum 1        
  default colormap:    0x20                           
  default number of colormap cells:    256            
  preallocated pixels:    black 0, white 16777215     
  options:    backing-store NO, save-unders NO        
  largest cursor:    64x64                            
  current input event mask:    0xfac031               
    KeyPressMask             EnterWindowMask          LeaveWindowMask          
    KeymapStateMask          ExposureMask             StructureNotifyMask      
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask          
    PropertyChangeMask       ColormapChangeMask                                
  number of visuals:    84                                                     
  default visual id:  0x21  

```

---

### Post by Giblet5 on 2009-11-06
Compiz should work OK for you.

The config options can get confused, especially if you upgraded to this release.

Something to try: create a test user account, log in as that user, then try setting up compiz the way you want it to be.

Does that work well?

It's easy to move your regular account's configuration aside and start over. ```
mkdir dotbackup
mv .gconf* .config dotbackup
sudo /etc/init.d/gdm restart
```

---

### Post by quimkaos on 2009-11-06
well seems to me that kde compiz has less features...

thing is:
gnome desktop is a mess, kde desktop is clean
gnome menus are well organized, kde menus are a mess
gnome gadjets are a mess, kde gadjets are ok
gnome compiz config is easy, kde compiz config is confusing and with less options...
my kde has no shutdown :lolflag:

stiking with gnome for now but not giving up on kde

---

### Post by Giblet5 on 2009-11-06
> **quimkaos said:**
> well seems to me that kde compiz has less features...

thing is:
gnome desktop is a mess, kde desktop is clean
gnome menus are well organized, kde menus are a mess
gnome gadjets are a mess, kde gadjets are ok
gnome compiz config is easy, kde compiz config is confusing and with less options...
my kde has no shutdown :lolflag:

stiking with gnome for now but not giving up on kde

You need to install the "plasma" plasmoids in kde, friend!

There is your shutdown gadget...

You can also right-click the desktop and select Leave... Pretty lame, though.

Yeah... Gnome has a messy desktop. KDE has a messy menu.

Why can't Spishak® save the day? They managed to make a floor wax that's also a dessert topping...

---

### Post by SuperSonic4 on 2009-11-06
You don't need compiz in KDE - KWin is more than adequate for the job.

Also Plasmoids are your friends and it would appear karmic does not have the *kshutdown* package which will shut down although I use the lock/logout plasmoid

---

### Post by Giblet5 on 2009-11-06
> **SuperSonic4 said:**
> You don't need compiz in KDE - KWin is more than adequate for the job.

Also Plasmoids are your friends and it would appear karmic does not have the *kshutdown* package which will shut down although I use the lock/logout plasmoid

I wrote my own. It prompts with "Restart", "Shutdown", and "Cancel" buttons. Restart calls "sudo reboot". Shutdown calls "sudo poweroff". Short. Simple. And kde better handle that SIGTERM quickly 'cause it only gets about five seconds to finish its sigterm handler before CARRIER LOST

---

### Post by quimkaos on 2009-11-06
now i would like to know what's the cleanest way to remove kde...

:biggrin:

---

