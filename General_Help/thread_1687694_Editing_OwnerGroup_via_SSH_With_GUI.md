---
title: "Editing Owner/Group via SSH With GUI?"
date: 2011-02-14
forum: General Help
---

### Post by TheFreakster on 2011-02-14
Hello all,

In Windows I used WinSCP to do all of my server work. It was easy and intuitive to use. In Ubuntu, I've been recommended to use  "sftp://" for the location. I can change folder permission settings this way, but it doesn't allow me to change the owner and group, and doesn't allow to change the file permissions (folder permissions are ok though).

Can anyone point me in the right direction? How do I go about doing this? I'm much more comfortable doing it via GUI rather than terminal.

Thanks.

---

### Post by TheFreakster on 2011-02-14
Hey, can anyone help me out with this? Surely there's a way to do this without using WinSCP via Wine?

Thanks a lot.

---

### Post by Habitual on 2011-02-14
Filezilla supports sftp mode connections and has a GUI. ;)

---

### Post by TheFreakster on 2011-02-15
> **Habitual said:**
> Filezilla supports sftp mode connections and has a GUI. ;)
Thanks for the reply.

I did forget to mention in my original post that I do have FileZilla and do use it as well. It also, though, doesn't have an owner/group option. It only allows chmod (by right clicking a file and selecting "File Permissions...").

Any other ideas?

---

### Post by tredegar on 2011-02-15
There's probably already a nautilus script that'll do this for you.

Look [here]("http://g-scripts.sourceforge.net/index.php") and read  their FAQ.

Then get **nautilus-scripts.tar.gz** from the same site. That contains a *lot* of scripts.

The **chmog** script looks a good candidate:
> #!/usr/bin/perl
# chmog
# A GUI for chown, chgrp and chmod. Requires perl and perl-gtk
#
# Distributed under the terms of GNU GPL version 2 or later
#
# Copyright (C) David Westlund <daw@wlug.westbo.se>
#


---

