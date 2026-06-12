---
title: "Properly close transmission on shut down"
date: 2010-02-07
forum: General Help
---

### Post by fabricio.lemos on 2010-02-07
If I log out or shut down Ubuntu with Transmission still open, the next time I start Transmission it will verify the local data, which take a very long time because I have lots of torrents.

Does anyone knows how I can prevent this without having to explicitly close Transmission every time?

If I explicitly close Transmission before shutting down Ubuntu, it works fine.

I'm using Ubuntu and 9.10 (Karmic Koala) and Transmission 1.75

thanks in advance,
Fabricio Lemos

---

### Post by ron999 on 2010-02-07
Try updating your Transmission to v1.83.

---

### Post by fabricio.lemos on 2010-02-07
How do I do that? The only package that I found was transmission_1.83-0ubuntu1_all.deb, but when I tried I got
Error: Dependency is not satisfiable: transmission-cli (>= 1.83-0ubuntu1)

---

### Post by NFblaze on 2010-02-07
Yea, ubuntu is slow on the updating of the Transmission repository.

There is an unofficial ppa provided by BalleClorin on the Transmission messageboards that I use with no issues available here [https://launchpad.net/~andreas-noteng/+archive/ppa](https://launchpad.net/~andreas-noteng/+archive/ppa)


Also, if you still have the problem you can try adding a kill script to your /etc/rc0.d/ . Im not all that advanced on how to do it but if you google runlevel script editing you can learn it.

---

### Post by ron999 on 2010-02-07
Hi
I'm sorry. I don't think that the Ubuntu repository has been updated yet.
I got information from this thread:-[http://ubuntuforums.org/showthread.php?t=1391718]("http://ubuntuforums.org/showthread.php?t=1391718")

Edit
Follow NFblaze advice above for ppa.

---

### Post by fabricio.lemos on 2010-02-07
I updated Transmission to v1.83 using Andreas Noteng ppa and still have the same problem :(

---

### Post by Charles Kerr on 2010-02-08
This is a known bug -- there's a [ticket for it in launchpad]("https://bugs.launchpad.net/ubuntu/+source/transmission/+bug/307684").
 
  The problem is the current way of handling shutdown notification in GNOME and GTK+ is going away, but nobody's decided yet on what its replacement should be.  So what's the Right Thing to do here?  It's frustrating.
 
  [this bug ticket post]("https://bugzilla.gnome.org/show_bug.cgi?id=79285#c26") from GNOME's bugzilla is a decent summary of the state of shutdown notification.

---

### Post by fabricio.lemos on 2010-02-08
Ok, thank you Charles. I did look at launchpad but didn't find this bug. Now I subscribed to it.

This problem is around for a long time, hope they correct it on next Gnome version.

---

### Post by BlueGene1402 on 2010-03-17
[FONT=Trebuchet MS][SIZE=2]I only wish that my Transmission *would* verify local data.

What happens with me is that if I fail to quit the application properly before shutting down my system is that anything downloaded in that session disappears on my next log in as if it never happened. It *says* it's verifying the local data but the latest downloads aren't there.

Even when I quit & restart or shut down 'healthily' as opposed to the electricity cutting off (don't ask) still the data verification is not fully functioning. It only reaches a smallish percentage then carries on still saying that there are for example 250MB of unverified data. That's a lot, considering my connection (again, don't ask lol) so every couple of days I'm losing hundreds of megabytes because they are not being "verified" even when I choose that option from the menu.

This also means that even if a file says it has reached 100% download I can't play it! Because it is not verified so it just **sits there** good for nothing..

I'm an absolute beginner even in torrents & don't know how these things work. Any suggestions? Thanks in advance.
[/SIZE][/FONT]

---

### Post by AggravatedGestalt on 2011-02-12
Mine only "verifies data" when I shutdown the system/reboot, or kill the PID. I have tried several kill options, and they all end up with transmission verifying data for a century or so. This may sound stupid, but if it is an open source program, why couldn't the same signal that transmission uses to shut itself down, be run through the shell?

---

### Post by AggravatedGestalt on 2011-02-12
> **BlueGene1402 said:**
> [FONT=Trebuchet MS][SIZE=2]
This also means that even if a file says it has reached 100% download I can't play it! Because it is not verified so it just **sits there** good for nothing..
[/SIZE][/FONT]
If it has reached 100%, you should be able to either right click on the torrent and open location; or more easily, navigate to /Places/Downloads and find it there. Even incomplete files often show up there.

---

### Post by imwithid on 2011-04-20
> **BlueGene1402 said:**
> [FONT=Trebuchet MS][SIZE=2]I only wish that my Transmission *would* verify local data.

What happens with me is that if I fail to quit the application properly before shutting down my system is that anything downloaded in that session disappears on my next log in as if it never happened. It *says* it's verifying the local data but the latest downloads aren't there.

Even when I quit & restart or shut down 'healthily' as opposed to the electricity cutting off (don't ask) still the data verification is not fully functioning. It only reaches a smallish percentage then carries on still saying that there are for example 250MB of unverified data. That's a lot, considering my connection (again, don't ask lol) so every couple of days I'm losing hundreds of megabytes because they are not being "verified" even when I choose that option from the menu.

This also means that even if a file says it has reached 100% download I can't play it! Because it is not verified so it just **sits there** good for nothing..

I'm an absolute beginner even in torrents & don't know how these things work. Any suggestions? Thanks in advance.
[/SIZE][/FONT]

Two things:

1. How is Transmission set in your Edit > Preferences as to your "Save to Location"? If this is set to a directory or drive that is not mounted at boot, your files will disappear into your "Paused" section with an error.

2. If the above is the case, simply mount the directory or drive prior to opening Transmission. If you have already opened Transmission by this point, the only way to fix it is to right click or highlight and click Torrent > Set Location, navigate to the appropriate folder and select "Local data is already there". From there, you can manually choose to "Verify Local Data".

To avoid this in future, set the "Save to Location" to your Home directory or a dedicated partition or drive that can be mounted at boot.


As mentioned previously, this has been a bug since I can remember first using Transmission a few years back. I don't expect this bug to be fixed any time soon as the activity on the aforementioned "ticket" has been sparse.

---

