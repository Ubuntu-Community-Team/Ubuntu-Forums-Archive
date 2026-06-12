---
title: "editing a shell script"
date: 2009-12-14
forum: General Help
---

### Post by chudder on 2009-12-14
Hi,

I installed OpenOffice from Sun, as opposed to the distro package.  There is a common error.  OO will start and then crash immediately.  According to their readme files, I need to enter the line unset SESSION_MANAGER in the soffice shell script code.

The problem with this is I don't know how to edit the shell script when it's read-only.  I can save another shell script but that defeats the purpose.

thank you

---

### Post by lmarmisa on 2009-12-14
Open a terminal.

If you are the owner of this shell script file type:

```

chmod +w shell_script_file
gedit shell_script_file

```

If root is the owner, type:

```

sudo chmod +w shell_script_file
sudo gedit shell_script_file

```

Best regards,

Luis

---

### Post by chudder on 2009-12-14
Thank you Luis, that worked as far as modifying the shell script.  It however didn't solve my OO problem, I posted a post on their forum as well.  Thanks for your help.

Chud

---

### Post by chudder on 2009-12-14
Now I got it working.  The link is: [http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=25612]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=25612")

Thanks to you and the OO forums, It's working now.

Chud

---

