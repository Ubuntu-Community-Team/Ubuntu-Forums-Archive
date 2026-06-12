---
title: "Software Center does not start. (It does with sudo)"
date: 2011-10-21
forum: General Help
---

### Post by FreaK2k on 2011-10-21
Hey,
here's the problem:
When I just click on Ubuntu-Software-Center nothing happens.

When I go to the console and type sudo software--center it starts without problems.

The next thing, and i think it's linked to the problem above is that the search for apps is not working. What for informations do you need to help me?
Thanks:(

---

### Post by deloquencia on 2011-10-21
Try to run the Software-Center without sudo in a console, whats the output? Looks like a problem with permissions so the debug switch will be unnecessary in this case. You should get some output from python and some error - as far as I hope.

---

### Post by rplantz on 2011-10-21
> **deloquencia said:**
> Try to run the Software-Center without sudo in a console, whats the output? Looks like a problem with permissions so the debug switch will be unnecessary in this case. You should get some output from python and some error - as far as I hope.

I am having the same problem. Here is my error message:
```

bob@bob-desktop:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 31, in <module>
    from gi.repository import GObject
ImportError: No module named gi.repository

```
I note that I changed python to point to python3 so it would be my default:
```

lrwxrwxrwx 1 root root      11 2011-10-20 08:52 /usr/bin/python -> python3.2mu
lrwxrwxrwx 1 root root       9 2011-10-20 08:51 /usr/bin/python2 -> python2.7
-rwxr-xr-x 1 root root 2735256 2011-10-04 14:26 /usr/bin/python2.7
lrwxrwxrwx 1 root root      11 2011-10-20 09:49 /usr/bin/python3 -> python3.2mu
lrwxrwxrwx 1 root root      11 2011-09-05 14:31 /usr/bin/python3.2 -> python3.2mu
-rwxr-xr-x 1 root root 3024320 2011-09-05 14:31 /usr/bin/python3.2mu

```
Could this be my problem? (Any idea what "mu" stands for?)

Edit: Changing my python links back to the original (python -> python2.7), and then rebooting, fixed my problem.

---

### Post by bjpend on 2011-10-22
> **FreaK2k said:**
> Hey,
here's the problem:
When I just click on Ubuntu-Software-Center nothing happens.

When I go to the console and type sudo software--center it starts without problems.

I have the same problem. I am using Oneiric and Unity.

Ubuntu Software Center started up  fine when I first upgraded to Oneiric several hours ago, but it stopped working after I used Synaptic - just to see if was there. I have no idea whether this is a coincidence.

Clicking on Ubuntu Software Center in the Unity launcher does nothing. The icon flashes a few times but nothing happens.

Here is the log of what happens when I try it from the terminal

```
mercury% software-center
2011-10-22 23:20:26,895 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
Traceback (most recent call last):
  File "/usr/bin/software-center", line 151, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 220, in __init__
    self.db.open(use_axi = self._use_axi)
  File "/usr/share/software-center/softwarecenter/db/database.py", line 200, in open
    self._axi_values = parse_axi_values_file()
  File "/usr/share/software-center/softwarecenter/db/database.py", line 48, in parse_axi_values_file
    for raw_line in open(filename):
IOError: [Errno 13] Permission denied: '/var/lib/apt-xapian-index/values'
mercury% 
mercury% 
mercury% sudo software-center
2011-10-22 23:20:31,768 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-10-22 23:20:32,471 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-10-22 23:20:32,597 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2011-10-22 23:20:39,519 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0


```I have tried rebooting, and I reinstalled Ubuntu Software Center from the command line, but neither seemed to have any effect.

*Added later:* I change the permissions on the file /var/lib/apt-xapian-index/values. Issuing* ls -l *from the command line used to return:

-rw-r----- 1 root root 853 2011-10-22 22:03 /var/lib/apt-xapian-index/values

Now it returns:

-rw-r--r-- 1 root root 853 2011-10-22 22:03 /var/lib/apt-xapian-index/values

After the change, I can start a Software Center window from the command line (without using sudo), and I get the menus and icons at the top of the window, but then Software Center just hangs.

It's not just a Unity problem, I get the same result using Unity2D, Gnome Classic and the Gnome Shell.

---

### Post by FreaK2k on 2011-10-25
Any new ideas how to solve this problem? Theres also a bug report to this topic now.

---

### Post by FreaK2k on 2011-10-25
Okay for me the problem is solved:

1. Navigate to your /home/USERNAME/.cache
2. Delete the folder software-center
3. restart the computer
4. be happy

---

### Post by deloquencia on 2011-10-28
Like this we won't get to know the exact problem... that's a bad solution :(

---

### Post by bjpend on 2011-10-29
My problem went away on its own. I didn't remove the cache and I didn't logout or restart, so I have no idea what fixed it.

---

### Post by rplantz on 2011-10-29
> **bjpend said:**
> My problem went away on its own. I didn't remove the cache and I didn't logout or restart, so I have no idea what fixed it.

Software is so complex these days, this sort of "fix" has become common. My system has at least two identifiable modes of behavior that come up randomly with each new boot.

Unity seems to have brought all sorts of problems to Ubuntu. I don't dislike Unity, but I don't see any advantage. It seems to be simply copying the phone/tablet interface to the desktop, but they are very different pieces of hardware. Sort of like putting a steering wheel on a bicycle so the interface will be more like a car.

I wish that designers would concentrate more on building better programs rather than adding new "features" that do not add to the utility of the system. I'm thinking of the way Heinrich Nordoff handled the VW Beetle from 1948 - 1968, "...improving the car's underpinnings while keeping the styling the same." (From wikipedia)

---

