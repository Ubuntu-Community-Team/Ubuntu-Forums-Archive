---
title: "nautilus crashes when inserting usb flash drive"
date: 2010-12-11
forum: General Help
---

### Post by Chris_82 on 2010-12-11
Hi there,

I am having some trouble with usb flash drive lately:
when plugging in:
[LIST]
[*] all nautilus windows close
[*] all icons disappear from the desktop but reappear seconds later
[*] after a couple of seconds of high cpu usage I can open a new nautilus windows and the drive is properly mounted.
[/LIST]

I have apport enabled:
[LIST]
[*] once in a while there is apport running and trying to gather a report which cannot be sent because it is an assert failure..
[*] once in a blue moon apport gives me the not-enough-memory error message ([screenshot here]("http://i1000.photobucket.com/albums/af128/rossch/Problem_in_nautilus.png?t=1292095476")) but I don't think it should need more than 400MB I had at that moment.
[/LIST]

dmesg gives this..:

```
[100146.868071] usb 1-4: new high speed USB device using ehci_hcd and address 8
[100147.003565] usb 1-4: configuration #1 chosen from 1 choice
[100147.021523] scsi6 : SCSI emulation for USB Mass Storage devices
[100147.028070] usb-storage: device found at 8
[100147.028078] usb-storage: waiting for device to settle before scanning
[100152.028299] usb-storage: device scan complete
[100152.029286] scsi 6:0:0:0: Direct-Access     SONY     Storage Media    1.00 PQ: 0 ANSI: 2
[100152.035097] sd 6:0:0:0: Attached scsi generic sg2 type 0
[100152.037484] sd 6:0:0:0: [sdb] 1015808 512-byte logical blocks: (520 MB/496 MiB)
[100152.038107] sd 6:0:0:0: [sdb] Write Protect is off
[100152.038118] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[100152.038126] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[100152.041609] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[100152.041621]  sdb: sdb1
[100152.052110] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[100152.052126] sd 6:0:0:0: [sdb] Attached SCSI removable disk
```

..which seems all fine to me.

I have searched launchpad bugs but was not lucky there.

Any ideas?
cheers.

---

### Post by TeoBigusGeekus on 2010-12-11
Open nautilus from terminal
```
nautilus
```
and see if you get any error messages.

---

### Post by Chris_82 on 2010-12-11
That was quick :D
> **TeoBigusGeekus said:**
> Open nautilus from terminal
```
nautilus
```
and see if you get any error messages.

Did that. Nope, no message at all.

---

### Post by Chris_82 on 2010-12-14
Update:

the same thing happens even when inserting a CD or an external USB harddisk.

cheers.

---

### Post by sefs on 2010-12-14
> **Chris_82 said:**
> Update:

the same thing happens even when inserting a CD or an external USB harddisk.

cheers.

If you turn off autorun for nautilus doe it still behave like this?

Autorun can be turned off via the gconf-editor, which can be launched by pressing ALT+F2, type "gconf-editor", without the quotes, into the textbox and clicking on run.  Then navigate apps > nautilus > preference and check media_autorun_never checkbox.

---

### Post by Chris_82 on 2010-12-14
> **sefs said:**
> If you turn off autorun for nautilus doe it still behave like this?

Yep this solves the issue.
It is more a workaround than a proper solution but at least I know what is causing it..
I knew about automount but not about autorun.

thanks :-)

ps: [filed a bug report on launchpad]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/690189").

---

### Post by sefs on 2010-12-14
> **Chris_82 said:**
> Yep this solves the issue.
It is more a workaround than a proper solution but at least I know what is causing it..
I knew about automount but not about autorun.

thanks :-)

I agree, you should try to reinstall nautilus from the repos and then re-enable autorun, assuming that the crashing behaviour comes from any removable media that you attach.

---

### Post by Chris_82 on 2010-12-14
> **sefs said:**
> I agree, you should try to reinstall nautilus from the repos and then re-enable autorun, assuming that the crashing behaviour comes from any removable media that you attach.

Did a apt-get remove --purge and then reinstalled but with no luck.
The crash stays.

---

### Post by sefs on 2010-12-14
Have you tested if the behaviour occurs with a live CD on the same system that is experiencing this problem?

---

### Post by TeoBigusGeekus on 2010-12-14
I'd also bleachbit the whole system - perhaps a broken cache file or something is causing the crash.

---

### Post by sefs on 2010-12-14
> **TeoBigusGeekus said:**
> I'd also bleachbit the whole system - perhaps a broken cache file or something is causing the crash.

...or some misset plugin or setting...but what is "bleachbit"  I have never heard of this?

---

### Post by TeoBigusGeekus on 2010-12-14
The CCleaner equivalent for linux (it has in fact a win version as well).
You can find it in the software center.

---

### Post by Chris_82 on 2010-12-14
> **TeoBigusGeekus said:**
> I'd also bleachbit the whole system - perhaps a broken cache file or something is causing the crash.
Just tried that.
The issue keeps sticking around..

> **sefs said:**
> Have you tested if the behaviour occurs with a live CD on the same system that is experiencing this problem?
I think that will work smoothly. I'll try.

By the way at first when I installed Lucid I didn't have the problem, it appeared sometime months ago..


thanks for the ideas :-)

---

### Post by Chris_82 on 2010-12-14
**bleachbit:**
Didn't help.
After a restart I could not login anymore through gdm, I had to reinstall gnome-session to get past that issue..
It seems bleachbit is a bit too aggressive with file deleting.

**live CD 10.4.1:**
Yep there the mounting works just fine (and the media_autorun_never key is false by default).

cheers.

---

### Post by sefs on 2010-12-15
> **Chris_82 said:**
> **bleachbit:**

**live CD 10.4.1:**
Yep there the mounting works just fine (and the media_autorun_never key is false by default).

cheers.

Well if you have time on your hands go thru and check each and every setting in the flaky version of nautilus preferences against the working one. :)

---

### Post by Chris_82 on 2011-01-13
> **sefs said:**
> Well if you have time on your hands go thru and check each and every setting in the flaky version of nautilus preferences against the working one. :)

Finally did that. Here is the outcome:
There are a lot of icon entries..
```
<entry>
      <key>desktop-metadata/1@46@0@32@GB@32@Filesystem@46@volume/icon-scale</key>
      <value>
        <string>1</string>
      </value>
    </entry>
```
..which don't seem harmful to me.

According to the diff between both configurations I have three additional keys on my system:
```

$ more gconf_naut.diff | grep "key" | grep -v "icon"
<key>desktop-metadata/directory/nautilus-window-scroll-position</key>
<key>preferences/navigation_window_saved_geometry</key>
<key>preferences/navigation_window_saved_maximized</key>

```

And these are the other keys with differing values:
From my conf:

[HTML]<key>preferences/default_folder_viewer</key>
      <schema_key>/schemas/apps/nautilus/preferences/default_folder_viewer</schema_key>
      <value>
        <string>list_view</string>
      </value>
<key>preferences/media_automount_open</key>
      <schema_key>/schemas/apps/nautilus/preferences/media_automount_open</schema_key>
      <value>
        <string>false</string>
      </value>
<key>preferences/media_autorun_never</key>
      <schema_key>/schemas/apps/nautilus/preferences/media_autorun_never</schema_key>
      <value>
        <bool>true</bool>
      </value>
<key>preferences/media_autorun_x_content_open_folder</key>
      <schema_key>/schemas/apps/nautilus/preferences/media_autorun_x_content_open_folder</schema_key>
      <value>
        <list type="string">
            <value>
              <string>x-content/image-dcf</string>
            </value>
<key>preferences/media_autorun_x_content_start_app</key>
      <schema_key>/schemas/apps/nautilus/preferences/media_autorun_x_content_start_app</schema_key>
      <value>
        <list type="string">
            <value>
              <string>x-content/software</string>
            </value>
            <value>
              <string>x-content/image-dcf</string>
            </value>
        </list>
      </value>
[/HTML]

Now I don't see how my nautilus configuration could be bad somewhere..

cheers.

---

### Post by juliobahar on 2011-02-09
I do have the same problem with Nautilus but not with USB flash drives. Recently and only recently, when I select all files (or press CTRL+A) in a folder with a vast array of files, the whole nautilus restarts, so does desktop icons. 
Tried some of the solutions in your post, no hope yet.

---

### Post by Chris_82 on 2012-03-16
> **juliobahar said:**
> .. when I select all files (or press CTRL+A) in a folder with a vast array of files, the whole nautilus restarts, so does desktop icons. Tried some of the solutions in your post, no hope yet.

Did you resolve this?
Your issue might not be related so I think it's best to open a new thread or even a bug report.
Also, [enable apport]("https://wiki.ubuntu.com/Apport") in case the bug gets caught by it.

ps: sorry for the late response.

---

