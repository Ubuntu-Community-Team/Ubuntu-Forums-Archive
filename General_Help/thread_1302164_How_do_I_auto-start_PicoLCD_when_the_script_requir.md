---
title: "How do I auto-start PicoLCD when the script requires GKSU?"
date: 2009-10-26
forum: General Help
---

### Post by slavojzizek on 2009-10-26
I want to automatically start the PicoLCD I have purchased on my Xubuntu machine. I need to do this because it will be a console-only startup (I have modified the system to not boot into the GUI). I can run the script provided when I am in GUI, and everything is cake. However, when I add the script to /etc/init.d and start my machine up it does not start in the same fashion.

The hardware details are [available here, along with manuals and drivers]("http://www.mini-box.com/picoLCD-256x64-OEM"). Yet, they do not mention anything about how to get the LCD to automatically turn on or start up. It currently shows that its powered on, but just displays the default splash screen.

I asked the maker of the hardware for help and they replied,

> 
Yes, but you will have to modify start-picolcd256x64.sh and use sudo instead of gksu or run it as a user who has permissions to do a kernel driver detach (root). Hope this information helps.



Could someone please help me out?

```

#!/bin/sh

# Script to run lcd4linux since you can't pass more then 1 parameter to InstallJammer shortcut creation function 
# we need a script for each shortcut

if [ $# -lt 1 ]
then
    INSTALL_PATH=$HOME/picolcd-256x64
else
    INSTALL_PATH=$1
fi

echo "Installation path: $INSTALL_PATH"

if [ ! -e $INSTALL_PATH/lcd4linux ] 
then
    echo -e "Cannot find lcd4linux executable file ! \nCheck if you installed the program correctly"
    exit 1
fi

WRAPPER="$INSTALL_PATH/picoLCDGraphic/picolcd-wrapper.sh $INSTALL_PATH lcd4linux.conf"
LD_LIBRARY_PATH=$INSTALL_PATH/picoLCDGraphic/Libs/:$LD_LIBRARY_PATH 
PYTHONPATH=$INSTALL_PATH/picoLCDGraphic/Scripts/:$PYTHONPATH

export GKSU_HELPER_DIR="$INSTALL_PATH/picoLCDGraphic/Libs/libgksu"
export LD_LIBRARY_PATH 
export PYTHONPATH

# picoLCD drivers need root access to detach from the kernel HID driver

if [ $USER != "root" ]
then
    echo "Running gksu wrapper"
    $INSTALL_PATH/picoLCDGraphic/gksu --message "picoLCD driver needs to be restarted"  "killall -9 lcd4linux"
    $INSTALL_PATH/picoLCDGraphic/gksu --message "picoLCD needs to detach from the kernel HID driver to function correctly" "$WRAPPER"
else
    killall -9 lcd4linux
    $INSTALL_PATH/lcd4linux -f $INSTALL_PATH/picoLCDGraphic/Configs/lcd4linux.conf -q
fi


```

---

### Post by mzuther on 2010-02-13
Hi slavojzizek,

I have directly installed lcd4linux from SVN, so I can only guess.  But I think you'll have to change the following lines:

```

    echo "Running gksu wrapper"
    $INSTALL_PATH/picoLCDGraphic/gksu --message "picoLCD driver needs to be restarted"  "killall -9 lcd4linux"
    $INSTALL_PATH/picoLCDGraphic/gksu --message "picoLCD needs to detach from the kernel HID driver to function correctly" "$WRAPPER"

```

to

```

    echo "picoLCD driver needs to be restarted"
    sudo killall -9 lcd4linux
    echo "picoLCD needs to detach from the kernel HID driver to function correctly"
    sudo "$WRAPPER"

```

Good luck,

Martin

P.S.: If you follow the section "USB port permissions" in the [lcd4linux FAQ]("http://ssl.bulix.org/projects/lcd4linux/wiki/FAQ"), you should be able to run lcd4linux as normal user:

```

    echo "picoLCD driver needs to be restarted"
    killall -9 lcd4linux
    echo "picoLCD needs to detach from the kernel HID driver to function correctly"
    "$WRAPPER"

```

---

