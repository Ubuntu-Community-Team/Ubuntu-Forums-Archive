---
title: "Evolution tree not expandable"
date: 2010-04-05
forum: General Help
---

### Post by Jonny787 on 2010-04-05
Hello experts,
after a simple backup of my Evolution e-mail (via File - Backup Settings...) the triangles left hand of an folder in the side bar (where you can expand in order to see subfolders) do not function anymore. The triangles are frozen to the status they where before backup.

So I have access to the subfolders which are open but no chance to get access to the subfolder which are not visible.
I tried already a restart, a second backup, I checked whether the files are read/write. But now I need help!

Does anyone know how I can get the triangles turning??

Thanks a lot!
/Jonny

---

### Post by helgeklemm on 2010-09-09
Hi,

I have exactly the same problem. There is a good description of the bug here:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/579082](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/579082)
But it seems no one is attending it. Are we only so few having that annoying problem?
BTW: I found a temporary workaround. You have to edit:
/home/user/.evolution/mail/config/folder-tree-expand-state.xml to your liking. Just add 'true' wherever necessary. If you select a folder in evolution that file gets immediately updated, so you can after a refresh figure out how that folder is named (which is complicated if IMAP).
Close evolution. Change file so that folder expand ist 'true'. Reopen evolution the folder is expanded.

In my case I created a backup which expands all my 3 folders holding subfolders. It looks like this:

<?xml version="1.0"?>
<tree-state>
  <node name="local" expand="true"/>
  <node name="vfolder" expand="true"/>
  <node name="gmail" expand="true"/>
<selected uri="imap://user%40gmail.com@imap.gmail.com:993/%5bGmail%5d/Gesendet"/><node name="1234567890.1234.1@XPS-Gamer" expand="true"><node name="[Gmail]" expand="true"/><node name="other Customers" expand="true"/></node></tree-state>

I know it's only a workaround, but at least, you can access your folders for the time being and continue working.

---

