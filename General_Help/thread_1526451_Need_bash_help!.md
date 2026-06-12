---
title: "Need bash help!"
date: 2010-07-08
forum: General Help
---

### Post by falven on 2010-07-08
Need some experienced with bash to help me please,
Aim: Sephirothfal
MSN: [EMAIL="falven2000@hotmail.com"]falven2000@hotmail.com[/EMAIL]

---

### Post by falven on 2010-07-08
Here is what I have been working on, I am brand new to bash scripting, any and all help is appreciated. If you can read bash code this should be self-explanatory?
Thanks,
-Falven

```
#!/bin/bash
# Bash script for installing the Adobe Flex SDK on Ubuntu.

PRODUCT="Flex SDK"
PLATFORM="Ubuntu"

echo ""
echo "$PRODUCT for $PLATFORM"
echo ""
echo "$PRODUCT $PLATFORM will be installed on this machine."

echo "This program will install the Flex SDK and its dependencies."
echo "Retrieving system information..."

sleep 1

OS=`uname -o`
FLAVOR=`uname -v`
if [[ $OS == *Linux* ] && [$FLAVOR == *Ubuntu*]];
then
    echo "$OS: Your Operating system is valid, continue? [Y/N]"
    read OPT
    if[[$OPT == y] || [$OPT == Y]];
        then
        for i in `seq 1 3`;
            do
                sleep 1
                echo "."
            done
        else
            echo "Quitting..."
            exit 0    
else
    echo "$ERR"
    exit 1
fi

echo "Retrieving Dependencies."

echo "Retrieving and installing Flex SDK."

mkdir /usr/lib/Flex-SDK
wget -v http://download.macromedia.com/pub/flex/sdk/flex_sdk_4.1.zip
unzip -dvo flex_sdk_4.1.zip usr/lib/Flex-SDK/
rm flex_sdk_4.1.zip

echo "Done."

sleep 1

echo "Retrieving and installing latest JDK."

cd /usr/lib
wget -v "http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/VerifyItem-Start/jdk-6u21-linux-i586.bin?BundledLineItemUUID=mMGJ_hCv0vgAAAEpYEsDzrDr&OrderID=DIKJ_hCvtr4AAAEpUksDzrDr&ProductID=LxaJ_hCy4mIAAAEpXLwzBGsB&FileName=/jdk-6u21-linux-i586.bin"
chmod +x jdk-6u21-linux-i586.bin
./jdk-6u21-linux-i586.bin
rm jdk-6u21-linux-i586.bin

echo "Done."

sleep 1

echo "Setting JAVA_HOME and PATH Environmental Variables"

for i in `seq 1 3`;
    do
        sleep 1
        echo "."
    done

echo "export JAVA_HOME=/usr/java/jdk1.6.0_21/bin/java" >> /etc/bash.bashrc
echo "export PATH=\$PATH:/usr/java/jdk1.6.0_21/bin:/usr/lib/Flex-SDK/bin" >> /etc/bash.bashrc

echo "Done."

sleep 1

echo "Removing old flash"

rm ~/.mozilla/plugins/libflashplayer.so 
rm ~/.mozilla/plugins/flashplayer.xpt

echo "Installing flash"
tar xzvf /usr/lib/Flex-SDK/runtimes/player/10.1/lnx/libflashplayer.so.tar.gz -C /usr/lib/mozilla/plugins/

echo "Installation Successfull"
echo "Finished!\n"

echo "A restart is required in order to properly configure the installation, restart now? [Y/N]"

read RST
if[[$RST == "y"] || [$RST == "Y"]];
then
    `shutdown -vr now`
else
    exit
fi
```

---

### Post by geirha on 2010-07-08
You need to learn the basic syntax of bash. You've got several syntax errors, so it seems you're simply guessing on syntax. That's not a good way to learn shell scripting. Read 
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
and then
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by falven on 2010-07-08
I already went through [this](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_01_01.html) whole guide, the stuff I need help with I can't find on-line...
I know PHP which seems to be very similar, and also bash has some Java attributes, I'm sure I would learn from my mistakes quickly if someone was courteous enough to point them out...?

---

### Post by geirha on 2010-07-09
> **falven said:**
> I already went through [this](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_01_01.html) whole guide, the stuff I need help with I can't find on-line...
I know PHP which seems to be very similar, and also bash has some Java attributes, I'm sure I would learn from my mistakes quickly if someone was courteous enough to point them out...?

The bash guides on tldp.org are unfortunately terrible for learning bash-scripting. [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) is the only really good bash guide around. So please read it.

To get you started on fixing that script, here's one where you've fallen into several of the [pitfalls](http://mywiki.wooledge.org/BashPitfalls):
```
if [[ $OS == *Linux* ] && [$FLAVOR == *Ubuntu*]];
```
That is wrong. [ ] are NOT part of the if-syntax, you can't just use [ ] as you would use parenthesis in C/java/php. If runs a **command** and checks the exit code of that command to determine whether the then block should be executed or not. See [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals), but preferably read the whole guide while you're there.

---

### Post by falven on 2010-07-09
Ok, sounds good I will read this guide since it seems to be a lot better, thank you for your reply. I will post back if I have any questions.
-Falven

---

