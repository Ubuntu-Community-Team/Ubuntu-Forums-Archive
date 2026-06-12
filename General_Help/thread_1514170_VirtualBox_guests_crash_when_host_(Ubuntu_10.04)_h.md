---
title: "VirtualBox guests crash when host (Ubuntu 10.04) hibernates"
date: 2010-06-20
forum: General Help
---

### Post by quadra on 2010-06-20
Some users experienced problems when the host hibernates while virtual machines are running on it.

In my case, my Ubuntu 10.04 host hibernates nicely, but when it resumes, virtual machines are reset and their state is lost.

Similar problems reported here:
[http://wwww.ubuntuforums.org/showthread.php?p=8630315]("http://wwww.ubuntuforums.org/showthread.php?p=8630315")
[http://ubuntuforums.org/showthread.php?t=405038]("http://ubuntuforums.org/showthread.php?t=405038")

---

### Post by quadra on 2010-06-20
Proposed solution: Save the virtual machine states before hibernating.

Save the following script e.g. at /home/USERNAME/bin/vbox_suspend. Make it executable:

```
# This script shall solve the problem that virtual machines are lost when hibernating Ubuntu host.
# For VirtualBox < v2.2.0, you may have to remove the -l (because format of 'list runningvms' changed)

for uuid in $(VBoxManage list runningvms -l | grep "UUID:            " | awk 'BEGIN{FS="UUID:            "}{print $2}')
do
        VBoxManage -nologo controlvm $uuid savestate
done 
```

You may test the script by executing it.

Put the following lines in /etc/pm/sleep.d/90virtualbox and make it executable as well (adapt path accordingly):
Not very elegant (as the user is hard-coded), but it works.

```
#!/bin/bash
case $1 in
        hibernate)
                su YOURUSER -c /home/YOURUSER/bin/vbox_suspend
                ;;
esac
```

---

### Post by teambob on 2010-07-19
Deleted: incorrect information

---

### Post by jazzgossen on 2010-08-29
Thanks a lot for these scripts.

Here is a variant of the sleep.d script that should work for multiple users, and also suspend to ram:

```
#!/bin/bash
for u in `users|sed -e 's/ /\n/g'|sort  -u`
do
    su $u -c /home/$u/bin/vbox_suspend
done
    
```

---

### Post by teambob on 2010-10-29
I created the vbox_suspend script in /usr/local/bin/vbox_suspend, rather than ~/bin/vbox_suspend.

Then I used the following as /etc/pm/sleep.d/90virtualbox:
```

#!/bin/bash
case $1 in
  hibernate|suspend)
    for u in `users|sed -e 's/ /\n/g'|sort  -u`
    do
      su $u -c /usr/local/bin/vbox_suspend
    done
    ;;
esac

```

---

### Post by cl3 on 2012-04-25
That script works for me (Linux Mint based on Ubuntu 11.04) if I name the file  02-VBox, the lower number leads to an earlier execution within the  hibernation process:
[http://angryfifer.blogspot.com/2012/02/linux-hibernation-and-virtualbox.html](http://angryfifer.blogspot.com/2012/02/linux-hibernation-and-virtualbox.html)

---

