---
title: "Trouble with Ubuntu Terminal Settings"
date: 2011-07-05
forum: General Help
---

### Post by dmubu on 2011-07-05
Hello,

I am a complete noob to Ubuntu.

When running my terminal, I notice it says systemdaniel2@daniel-MXC061.  What is the MXC061 part?

I do not believe that my terminal always said this.  I recently configured SSH, at which point the MXC061 was appended to the account name.

I removed SSH and want to configure from scratch, but -MXC061 is still appearing.  Is there any way to restore the original terminal settings (i.e., with the original user info)?

Thank you so much!

---

### Post by Dangertux on 2011-07-06
> **dmubu said:**
> Hello,

I am a complete noob to Ubuntu.

When running my terminal, I notice it says systemdaniel2@daniel-MXC061.  What is the MXC061 part?

I do not believe that my terminal always said this.  I recently configured SSH, at which point the MXC061 was appended to the account name.

I removed SSH and want to configure from scratch, but -MXC061 is still appearing.  Is there any way to restore the original terminal settings (i.e., with the original user info)?

Thank you so much!

The format for that is 

username@hostname

So daniel-MXC061 is your machine's hostname.

If you want to change that you can edit your hosts file
```

gksu gedit /etc/hosts

```

You will see a line like this. 
```

127.0.1.1    daniel-MXC061

```
Change the daniel-MXC061 to whatever you'd like (note if you have anything on your network that connects via hostname it will have to be updated to reflect this as well)

Once you do that you need to restart a couple of services (or just reboot your machine)
```

sudo /etc/init.d networking restart
sudo invoke-rc.d gdm restart

```

Note the last command will restart xserver so make sure that you have saved everything you are working on prior to issuing it.

---

### Post by dmubu on 2011-07-06
Thank you so much for your response.

I edited the text file to say the following:

127.0.0.1 localhost    
127.0.1.1 daniel


I saved the file, closed out and received the following message in the terminal:

(gedit:1869): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1869): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.GI58XV': No such file or directory

(gedit:1869): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1869): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Z4E6XV': No such file or directory

(gedit:1869): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

I then restarted the machine.  Upon entering the terminal the same user info appears even though the text file has been edited.

Any thoughts?

Thanks again for your help.  I really appreciate it!

---

### Post by Dave_L on 2011-07-06
In addition to /etc/hosts, you also have to change /etc/hostname.

---

### Post by dmubu on 2011-07-06
Thanks a lot!  That worked!

Just out of curiosity, do you know what the default user display in the terminal is when you first install Ubuntu?

I was fooling around with SSH and this is how it got changed in the first place.  If it was previously displaying as systemdaniel2@daniel-MXC061, would the default just be systemdaniel2 (i.e., with no "@")?

Thanks again for figuring this out for me!

---

### Post by nothingspecial on 2011-07-06
It's controlled by the $PS1 variable in your .bashrc

The default is user@host:path/to/working/directory $

Sometimes, when I'm working way down the tree the path takes up the whole line which makes things difficult, so I type

```
export PS1='$ '
```

which makes my prompt look like this

$

Then when I want it back to normal, I just get bash to read my .bashrc again

```
. ~/.bashrc
```

---

### Post by dmubu on 2011-07-06
Thank you!

I appreciate all the help...

---

