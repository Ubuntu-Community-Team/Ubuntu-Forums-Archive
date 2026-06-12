---
title: "making a shell script run with root AND non-root priveledges"
date: 2010-07-28
forum: General Help
---

### Post by HyperFlexed on 2010-07-28
Hi, I have a bit of a dilemma.

I'm using XFCE and it doesn't by default lock the screen before hibernating. I see this as a bit of a security risk, and as I can't hibernate while the screen is locked, I'm a bit lost as to how to achieve this.

I've begun editing /etc/acpi/hibernate.sh, here's what I have so far:
```
#!/bin/bash
# TODO:  Above should be /bin/sh

test -f /usr/share/acpi-support/state-funcs || exit 0

. /etc/default/acpi-support

if [ x$ACPI_HIBERNATE != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

#
# lock screen for xfce4 (stupid thing won't do it on its own)
#

# see if xfdesktop is running (so as to not interfere with GNOME, KDE,
# etc.
ps aux | grep xfdesktop > /dev/null

# if grep returned 0, xfdesktop is running, so we can safely work
# this little kludge
if [ $? -eq 0 ]; then
  #logger "xfdesktop was running during call to hibernate"
  echo debug: calling gnome screensaver lock
  gnome-screensaver-command --lock
  echo debug: gnome screensaver lock called
fi

echo debug: calling pm-hibernate
pm-hibernate
echo debug: pm-hibernate called
```

If I run this command with my user account, gnome-screensaver will lock the screen, but pm-hibernate will say that it needs to be run with root privileges.

If I run with sudo, the system hibernates, but gnome-screensaver will not fire. I can verify this by trying "sudo gnome-screensaver-command --lock". The screen goes black, but is not locked. The screen locks properly without sudo.

So the only solution I can see is to edit /etc/acpi/hibernate.sh in such a way that gnome-screensaver-command runs under the current user, and pm-hibernate is called as root.

Also, when I click the HIBERNATE button in XFCE, how does it call pm-hibernate under root without prompting me for a password? I normally wouldn't be interested in such things, but as it seems relevant to my problem I'm a little more eager to learn :)

---

### Post by prodigy_ on 2010-07-28
You can run the whole script as root and use **sudo -u** to execute a singe command as a different user:
```
sudo -u <your_user_name> gnome-screensaver-command --lock
```

---

### Post by HyperFlexed on 2010-07-28
I've tried testing that theory with the following script:

**sudo-test.sh**
```
sudo -u `whoami` gnome-screensaver-command --lock
```

if I run: ./sudo-test.sh, the screen locks
if I run: sudo ./sudo-test.sh, the screen does NOT lock

it seems that the sudo called when running the script overrides the "sudo -u"... unless `whoami` is returning root because the script was called with sudo?

Any idea how I can use a command to see who invoked the script with sudo?

i.e. bob@computar: sudo thescript.sh, and in thescript.sh, there's some kind of command that will return the value "bob"?

---

### Post by prodigy_ on 2010-07-28
Like you guessed ```
sudo whoami
``` returns **root**. You can use some trick however. For example:

```
USER_NAME=$(who -m|cut -d' ' -f1)
sudo -u ${USER_NAME} gnome-screensaver-command --lock
```

---

