---
title: "autostart a password requird .sh file"
date: 2009-10-23
forum: General Help
---

### Post by jackel7007 on 2009-10-23
Currently I'm trying to autorun a program called OAST.
This program is exactly what we need due to it's simple GUI and ability to connect you to a VPN tunnel whilst your normal internet connection also keeps active. So it's not Or Or but And..

When starting the program, root password is required....
I would like to make the program auto start, i achieved this by adding the program to system --> autostart.

This results in an password prompt at startup.

I have been trying to add the program to the sudoers file, but it fails and still requires the password:

The sh file:
/home/jack/OAST/oast.sh

in this file we find this:

> #!/bin/bash
OAST="java -cp ./:./lib/swt-3.4-gtk-linux-x86.jar splash.splash"
LUID=$(id -u)
if [[ $LUID -ne 0 ]]; then
    if which gksudo &> /dev/null; then
    gksudo -u root "$OAST"
    exit 0
    else
        if which gnomesu &> /dev/null; then
        gnomesu -u root -c "$OAST"
        exit 0
        else
            if which kdesu &> /dev/null; then
            kdesu -u root -c "$OAST"
            else
            xmessage -center -buttons "   OK   " "Please install gksudo/gnomesu/kdesu."
            fi
        fi
    fi
else
$OAST
fi

So the Shell script runs java which opens the /lib/swt-3.4-gtk-linux-x86.jar file

I have added the following rules to sudoers (one by one) and also all at once just to be sure:

> ALL ALL = NOPASSWD: /home/jack/OAS/oast.sh
ALL ALL = NOPASSWD: /usr/bin/java
ALL ALL = NOPASSWD: /home/jack/OAS/lib/swt-3.4-gtk-linux-x86.jar
 jack ALL = NOPASSWD: /home/jack/OAS/oast.sh
jack ALL = NOPASSWD: /usr/bin/java
jack ALL = NOPASSWD: /home/jack/OAS/lib/swt-3.4-gtk-linux-x86.jar

Whatever I do, it keeps asking me for the password at start.

Who can, and is willing to help?

---

### Post by Giblet5 on 2009-10-23
Try opening a terminal and executing this: ```
gksu nautilus
```

It should have asked you for your password.

Is that the same (identical) password prompt that Oast presents?

---

### Post by jackel7007 on 2009-10-23
yes it's identical..

The script must be starting openvpn too.
openvpn normally requires sudo to start it, so maybe that is the root of my problem?

---

### Post by undecim on 2009-10-23
> **Giblet5 said:**
> Try opening a terminal and executing this: ```
gksu nautilus
```It should have asked you for your password.

Is that the same (identical) password prompt that Oast presents?

The script executes gksudo, so yes, it would be the same.

The easiest thing to do would probably be to make the entire script run as root (i.e. add the script path to sudoers, and make the file read only to everyone except root)

EDIT: Make sure to prefix the auto-start command with "gksu" if you are going with the route I just explained

---

### Post by jackel7007 on 2009-10-23
I think what you mean is the thing i tried (see the start post)...

---

### Post by undecim on 2009-10-23
> **jackel7007 said:**
> I think what you mean is the thing i tried (see the start post)...
You need to be trying to run the script as root though (by prefixing the start-up command with gksu)

---

### Post by albandy on 2009-10-23
> **jackel7007 said:**
> Currently I'm trying to autorun a program called OAST.
This program is exactly what we need due to it's simple GUI and ability to connect you to a VPN tunnel whilst your normal internet connection also keeps active. So it's not Or Or but And..

When starting the program, root password is required....
I would like to make the program auto start, i achieved this by adding the program to system --> autostart.

This results in an password prompt at startup.

I have been trying to add the program to the sudoers file, but it fails and still requires the password:

The sh file:
/home/jack/OAST/oast.sh

in this file we find this:



So the Shell script runs java which opens the /lib/swt-3.4-gtk-linux-x86.jar file

I have added the following rules to sudoers (one by one) and also all at once just to be sure:



Whatever I do, it keeps asking me for the password at start.

Who can, and is willing to help?


1.- create a new script for test in /usr/local/bin called test with this contents:

#!/bin/bash
java -cp ./:./lib/swt-3.4-gtk-linux-x86.jar splash.splash #(use the absolute path not a relative path)

2.- add execution perms to the script:
sudo chmod 755 /usr/local/bin/test

3.- Add the script to the sudoers file this way:
%testgroup ALL = NOPASSWD: /usr/local/bin/test

4.- add your user to testgroup
sudo adduser yourusername testgroup

5.- Exit your session and log in again
6.- open a console and type:
/usr/local/bin/test
7.- Tell us if it's still asking a password
8.- If works add this line to the autorun config:
/usr/bin/sudo /usr/local/bin/test
9.- add any user who need to use this software to "testgroup"

---

### Post by jackel7007 on 2009-10-23
Well that did (half) the trick..
OAST starts without a password now, and all seems fine.
But, since OAST is "Openvpn Agent and Setup Tool"

it now tries to execute all the commands behind the stage without root acces.
thus, openvpn isn't working as it should

I have added openvpn to my visudo, and again one step further, but it now has trouble creating the tunnel.

So i added the ifconfig (which I thought was used to create a tunnel) to visudo, but yet another error:

> Fri Oct 23 16:53:20 2009 Cannot allocate TUN/TAP dev dynamically

Seems that I first have to make openvpn commandline fully functional without sudo-ing it...

So now running the openvpn command line returns me:
Fri Oct 23 16:54:16 2009 Cannot allocate TUN/TAP dev dynamically
Fri Oct 23 16:54:16 2009 Exiting

---

### Post by jackel7007 on 2009-10-26
seems that it did not do the trick...
If i remove the line from visudo, i can still run that script... and it isn't working either.
If i run the script by placing sudo in front of it, all goes well.

How can I run this script in sudo mode without adding sudo to it?
I thought this was normally done by adding it to sudoers using visudo, i used this line to add it:

jack ALL = NOPASSWD: /home/jack/OAST/oast.sh

But if I run the command with SUDO in front of it, it still asks for the password (which is normal i guess) but if I run the command without sudo, it doesn't work. 
Because it fails to create the vpn tunnel.

So how can I run the oast.sh as sudo (in such a way that all the following command's are also executed as sudo)

---

