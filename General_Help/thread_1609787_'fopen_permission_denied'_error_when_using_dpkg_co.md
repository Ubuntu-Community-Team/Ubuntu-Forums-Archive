---
title: "'fopen: permission denied' error when using dpkg command"
date: 2010-10-30
forum: General Help
---

### Post by olivaw_daneel on 2010-10-30
I've downloaded a .deb file and I'm trying to install it using dpkg -i.

However, when I do this I get the following output:

```
Setting up usb-modeswitch (1.1.0-2) ...
Processing triggers for man-db ...
fopen: Permission denied
```

Obviously I'm using sudo to install the file.

I searched for this error on Google and found a post from someone saying to do:

```
chown -R man:root /var/cache/man
```

The permissions change when I do this but unfortunately I still get the same error when installing the .deb file.

Any help would be much appreciated.

---

### Post by utnubuuser on 2010-10-30
did you open the tarball and have a look at the README file to see if there are specific instruction?

---

### Post by _khAttAm_ on 2010-10-30
deb file please.

---

### Post by olivaw_daneel on 2010-10-31
The file is 'usb-modeswitch_1.1.0-2_i386.deb'

I found a readme but it doesn't contain any specific instructions.

---

### Post by Vigh on 2010-10-31
you running 64-bit? try sudo dpkg -i -force-all 'yourfile.deb'
enter password- hit enter

---

### Post by olivaw_daneel on 2010-10-31
> **Vigh said:**
> you running 64-bit? try sudo dpkg -i -force-all 'yourfile.deb'
enter password- hit enter

No I'm not running 64-bit. Will that code work anyway?

---

### Post by Hippytaff on 2010-10-31
You should be able to just double click on the .deb file to execute it. You might have to change mode to executable?

```

sudo chmod +x filename.deb

```

---

### Post by olivaw_daneel on 2010-10-31
> **Hippytaff said:**
> You should be able to just double click on the .deb file to execute it. You might have to change mode to executable?

```

sudo chmod +x filename.deb

```

I changed the permissions like you said but still getting the same error.

When I double click on the file it executes and says it has been installed but when I look in the terminal it still says 'fopen: permission denied'.

---

### Post by Hippytaff on 2010-10-31
If it's already install you should just be able to use it.
Test to see if you can read the help file
```

usb_modeswitch --help

```

---

### Post by olivaw_daneel on 2010-10-31
> **Hippytaff said:**
> If it's already install you should just be able to use it.
Test to see if you can read the help file
```

usb_modeswitch --help

```

Yes it does seem to install although I don't think it is installing fully.

When it installs it should create a file called 'usb_modeswitch.conf' in my /etc folder. But there's nothing there.

I'm guessing that because I get this 'fopen: permission denied' error it's not installing everything although I don't know enough about it to say this for sure.

---

### Post by Hippytaff on 2010-10-31
have you tried uninstalling it (purge) then installing it as root (sudo)

---

### Post by mc4man on 2010-10-31
Out of curiousity - does this machine not have an internet connection or is there some other reason you aren't using apt-get, synaptic or the software center to install?

---

### Post by olivaw_daneel on 2010-10-31
> **Hippytaff said:**
> have you tried uninstalling it (purge) then installing it as root (sudo)

Um I think so.

I uninstalled the package from ubuntu software centre and then installed it again from:

```
sudo su
```

then 

```
dpkg -i 'filename.deb'
```

> **mc4man said:**
> Out of curiousity - does this machine not have an internet connection or is there some other reason you aren't using apt-get, synaptic or the software center to install?

Yes I recently moved into a new flat and won't have a "proper" internet connection for 2-3 weeks. I've been downloading the .deb packages on windows and then transferring them across via usb stick to ubuntu. 

I'm trying to get my Huawei e1750 usb stick to work with ubuntu.

---

### Post by mc4man on 2010-10-31
> When it installs it should create a file called 'usb_modeswitch.conf' in my /etc folder. But there's nothing there.
I don't use lucid but, ....
the usb-modeswitch package for lucid does not contain a usb_modeswitch.conf file which may or may not be an issue (neither does the ..data package
see here
[http://packages.ubuntu.com/lucid/usb-modeswitch/filelist](http://packages.ubuntu.com/lucid/usb-modeswitch/filelist)

By contrast both the karmic and maverick packages do
ex. maverick
[http://packages.ubuntu.com/maverick/usb-modeswitch/filelist](http://packages.ubuntu.com/maverick/usb-modeswitch/filelist)

Now I don't use so not sure if one is needed to use, the conf in maverick is quite sparse, maybe run usb_modeswitch --help or man usb_modeswitch  for usage

If it does need one I'd try dl'ing the maverick deb, extract it and then copy the file to /etc ( or karmic's
Or file a bug

---

### Post by olivaw_daneel on 2010-10-31
> **mc4man said:**
> I don't use lucid but, ....
the usb-modeswitch package for lucid does not contain a usb_modeswitch.conf file which may or may not be an issue (neither does the ..data package
see here
[http://packages.ubuntu.com/lucid/usb-modeswitch/filelist](http://packages.ubuntu.com/lucid/usb-modeswitch/filelist)

By contrast both the karmic and maverick packages do
ex. maverick
[http://packages.ubuntu.com/maverick/usb-modeswitch/filelist](http://packages.ubuntu.com/maverick/usb-modeswitch/filelist)

Now I don't use so not sure if one is needed to use, the conf in maverick is quite sparse, maybe run usb_modeswitch --help or man usb_modeswitch  for usage

If it does need one I'd try dl'ing the maverick deb, extract it and then copy the file to /etc ( or karmic's
Or file a bug

Maybe you're right. When I do usb_modeswitch --help there is an option to set a config. Problem is I'm not really sure how I'm supposed to use it. When I type usb_modeswitch --help I get this:

```
Usage: usb-modeswitch [-hvpVPmMrdHn] [-c filename]

 -h, --help                    this help
 -e, --version                 print version number and exit
 -v, --default-vendor NUM      vendor ID to look for (mandatory)
 -p, --default-product NUM     product ID to look for (mandatory)
 -V, --target-vendor NUM       target vendor (optional, for success check)
 -P, --target-product NUM      target model (optional, for success check)
 -C, --target-class NUM        target device class
 -m, --message-endpoint NUM    where to direct the message (optional)
 -M, --message-content <msg>   command to send (hex number as string)
 -n, --need-response           read a response to the message transfer
 -r, --response-endpoint NUM   where from read the response (optional)
 -d, --detach-only             just detach the storage driver
 -H, --huawei-mode             apply a special procedure
 -S, --sierra-mode             apply a special procedure
 -O, --sony-mode               apply a special procedure
 -G, --gct-mode                apply a special procedure
 -R, --reset-usb               reset the device in the end
 -c, --config <filename>       load different config file
 -Q, --quiet                   don't show progress or error messages
 -W, --verbose                 print all settings before running
 -D, --sysmode                 specific result and syslog message
 -s, --success NUM             check switching result after NUM secs
 -I, --no-inquire              do not get device details (default on)

 -i, --interface NUM           select initial USB interface (default 0)
 -u, --configuration NUM       select USB configuration
 -a, --altsetting NUM          select alternative USB interface setting


```

If I type 

```
usb_modeswitch --config <filename>
```

I get the following error:

```
No default vendor/product ID given. Aborting.
```

If I try usb_modeswitch --default-vendor NUM I get the same error message.

Thanks.

---

### Post by Hippytaff on 2010-10-31
probably best to read the man page for usb_modeswitch but I think if you do. Here is my usb_modswitch.conf (etc/usb_modeswitch.conf)
```

# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>"

EnableLogging=0

```

just the options to switch logging off and to disable switching.

---

### Post by olivaw_daneel on 2010-11-01
Thanks for your help. It's sorted now.

---

### Post by Hippytaff on 2010-11-01
How did you fix it, so others can benefit :-)

Also remember to mark the thread as solved :-)

---

### Post by olivaw_daneel on 2010-11-02
> **Hippytaff said:**
> How did you fix it, so others can benefit :-)

Also remember to mark the thread as solved :-)

Well the original issue I started this thread with turned out not be an issue at all. The usb modeswitch deb package for lucid doesn't have a usbmodeswitch.conf file.

However, it is possible to configure usbmodeswitch in lucid by typing:

```
usb_modeswitch -v <vendor ID of usb modem> -p <product ID of usb modem>
```

And then whatever command you want after that e.g.

```
usb_modeswitch -v 0x12d1 -p 0x1001 -d 1
```

This code will detach the storage driver for a huawei e620.

I still continued to get the 'fopen: permission denied' error although it didn't matter in this case.

---

