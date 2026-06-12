---
title: "I got a shell script I would like help with"
date: 2010-10-08
forum: General Help
---

### Post by hart02 on 2010-10-08
Based on the instructions of master kernel thread I made a shell script for compiling a kernel.
```
#!/bin/sh
YELLOW="\033[1;33m"
RED="\033[0;31m"
ENDCOLOR="\033[0m"
echo -e $RED"I will stop with CTRL + C ."$ENDCOLOR
echo -e $YELLOW"I am getting required packages if they are not present."$ENDCOLOR
sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev
echo -e $YELLOW"I will go to the Source directory."$ENDCOLOR
cd /usr/src
echo -e $YELLOW"I will download and open the Source file."$ENDCOLOR
#sudo wget -c http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.35.tar.bz2 && tar -xvjf linux-2.6.35.tar.bz2
sudo apt-get install linux-source
echo -e $YELLOW"I will make a needed directory if it's not present for the Source."$ENDCOLOR
sudo mkdir /etc/kernel/postrm.d/
echo -e $YELLOW"I am copying neccesary files for the Source to use if they are not present."$ENDCOLOR
sudo cp /usr/share/kernel-package/examples/etc/kernel/postinst.d/initramfs  /etc/kernel/postinst.d/ 
sudo cp /usr/share/kernel-package/examples/etc/kernel/postrm.d/initramfs  /etc/kernel/postrm.d/
echo -e $YELLOW"I removing old symlinks to make a new one. I will then go to the Source."$ENDCOLOR
sudo rm -rf linux && ln -s /usr/src/linux-2.6.35 linux && cd /usr/src/linux
echo -e $YELLOW"I will copy your boot configuration for the Source."$ENDCOLOR
sudo cp /boot/config-$(uname -r) .config && yes "" | make oldconfig
echo -e $YELLOW"I conform the source to your hardware."$ENDCOLOR
sudo make localmodconfig
echo -e $YELLOW"I will be sending you to a menu for you to make any final adjustments to the Source.You can exit the menu if you are fine with the configuration of the Source."$ENDCOLOR
sudo make menuconfig
echo -e $YELLOW"I will clean the Source."$ENDCOLOR
sudo make-kpkg clean
echo -e $YELLOW"I will now compile the Source."$ENDCOLOR
sudo INSTALL_MOD_STRIP=1 CONCURRENCY_LEVEL=3 fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers kernel_debug kernel_manual kernel_source modules_image 
echo -e $YELLOW"I will now exit and install the Source."$ENDCOLOR
cd .. && sudo dpkg -i linux-image*2.6.35*.deb
echo -e $RED"I am done. Now reboot to use your new kernel and may the Source be with you."$ENDCOLOR
exit 0
```


Now i am thinking if I had non free drivers, I would want to be able to select those.I thought about incorporating sdennie's nvidia script from here. Then some ability for input so I could change the version name. I am also not getting color text I want. I would make the options yellow and the non options red. any help would be appreciated.

---

### Post by bodhi.zazen on 2010-10-08
[http://linuxgazette.net/issue65/padala.html](http://linuxgazette.net/issue65/padala.html)

[http://www.faqs.org/docs/abs/HTML/colorizing.html](http://www.faqs.org/docs/abs/HTML/colorizing.html)

[http://linux.byexamples.com/archives/184/print-text-in-colors-with-a-simple-command-line/](http://linux.byexamples.com/archives/184/print-text-in-colors-with-a-simple-command-line/)

---

### Post by asmoore82 on 2010-10-09
You are using the plain "sh" shell instead of "bash"
The shell's built-in `echo` command supersedes the `/bin/echo` program.
The built-in `echo` in "sh" doesn't appear to support the "-e" switch.

Technically, your references to the color variables should be within the quotation marks.
To prevent the variable names from getting confused with the surrounding text,
use the full unambiguous variable reference form *"${variable}"*.

That having been said, the full "bash" shell with `echo -e` seems to be
very forgiving with the variable references outside of the quotations.

I really like how you are abstracting the color codes to enhance readability.
I would suggest taking it a step further...
Here's a sort of "mark-up language" approach implemented as a replacement `echo` function:
The catch is you'll have to move to the full bash shell for it to work -
"sh" doesn't support functions...
```
#!/bin/bash

function echo ( )
{
	echo="builtin echo"
	if [ "$1" = "-n" ]
	then
		echo="$echo -n"
		shift
	fi
		
	message="$*_NORMAL_"
	message="${message//_WHITE_/\\033[1;37m}"
	message="${message//_RED_/\\033[1;31m}"
	message="${message//_GREEN_/\\033[1;32m}"
	message="${message//_BLUE_/\\033[1;34m}"
	message="${message//_YELLOW_/\\033[1;33m}"
	message="${message//_PURPLE_/\\033[1;35m}"
	message="${message//_NORMAL_/\\033[0m}"

	$echo -e "$message"
}
```

The only side effect is that `echo` is always `-e`,
this can be worked around with a `builtin echo` call, if necessary.

I was careful to hack in support for `-n` - as this may be useful for prompts.

Examples of this function in use:
```
$ echo "_RED_red, _WHITE_white, _NORMAL_and _BLUE_blue."
[COLOR="Red"]red,[/COLOR] [COLOR="White"]white,[/COLOR] and [COLOR="Blue"]blue.[/COLOR]
$ echo "_YELLOW_bananas, _PURPLE_grapes, _NORMAL_and _RED_apples."
[COLOR="Yellow"]bananas,[/COLOR] [COLOR="Purple"]grapes,[/COLOR] and [COLOR="Red"]apples.[/COLOR]
$ echo -n "_YELLOW_Please, enter a _RED_number_YELLOW_? "
[COLOR="Yellow"]Please, enter a[/COLOR] [COLOR="Red"]number[/COLOR][COLOR="Yellow"]?[/COLOR] 
```

Of course, all this isn't very efficient, but if you're compiling
the whole kernel, a fancy `echo` function should hardly be the bottleneck =D.

---

