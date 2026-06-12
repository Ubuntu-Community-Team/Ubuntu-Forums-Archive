---
title: "Update Manager error - NO PUBKEY"
date: 2010-02-09
forum: General Help
---

### Post by Corporate Boy on 2010-02-09
I just ran executed the Update manager and received the following error message -

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Anyone encountered this problem?

I am in process of diagnosing other problems with my Ubuntu laptop.  I just started this thread which has to do with files disappearing.

[http://ubuntuforums.org/showthread.php?t=1403063](http://ubuntuforums.org/showthread.php?t=1403063)

---

### Post by sisco311 on 2010-02-09
you have to add medibuntu's public key to the list of trusted keys:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0C5A2783
```

[uhelp]community/Medibuntu[/uhelp]

---

### Post by crichard on 2010-02-09
You need to authorize your pub key by executing the following commands,
Goto terminal,
> 
gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783

> gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -

> sudo apt-get update

That's it. :)

---

### Post by Corporate Boy on 2010-02-09
Thanks for the help.  The update mgr was working for me, but it stopped working for some reason.  Do you know what cause the key to be deleted?  I don't know what I did to cause it.  I uninstalled flash 9 from the command line and then reinstalled Flash 10.


>   1  sudo apt-get install ia32-libs nspluginwrapper
    2  wget [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz)
    3  tar zxvf flashplayer10_install_linux_051508.tar.gI z
    4  sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
    5  rm -rf ~/install_flash_player_10_linux/cd ~
    6  wget [http://download.macromedia.com/pub/labs/flashplayer10/](http://download.macromedia.com/pub/labs/flashplayer10/)
    7  exitI might have tried some other command lines.  I should  have kept better track.

Thanks for your help.

---

### Post by Corporate Boy on 2010-02-10
The upgrade manager still appears to work fine, so I would consider this problem resolved.  Although I still plan to format and reinstall because  I don't know how I got into this state and I am still experiencing weirdness with lost files.

---

