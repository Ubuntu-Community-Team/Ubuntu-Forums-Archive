---
title: "Why doesn't startupmanager open for me in Natty.?"
date: 2011-10-02
forum: General Help
---

### Post by inameiname on 2011-10-02
I cannot seem to open startupmanager via Main Menu, or via "su-to-root -X -c /usr/sbin/startupmanager". I only seem to get this message, upon attempting to open startupmanager via the terminal:

```

$ su-to-root -X -c /usr/sbin/startupmanager

(gksu:3422): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
    'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
  File "/usr/sbin/startupmanager", line 54, in <module>
    main()
  File "/usr/sbin/startupmanager", line 51, in main
    SumGui()
  File "/usr/share/startupmanager/gtk_frontend.py", line 166, in __init__
    self.resolution = utils.get_resolution()
  File "/usr/lib/pymodules/python2.7/bootconfig/utils.py", line 159, in get_resolution
    return matches.group(1) + 'x' + matches.group(2)
AttributeError: 'NoneType' object has no attribute 'group'

```I am unsure what to make of this, so figured I would ask here to see if anybody else can help.

I did read once upon a time ago startupmanager does not work well with the newer grub. Although, if that is it, this why would there be a Natty version of it?

FYI, I am using this version of startupmanager: 1.9.13-6~eugenesan~natty2 .

---

### Post by inameiname on 2011-10-02
Nevermind. It was in fact my version of startupmanager. Oops...hehe. I always feel bad for figuring my issue out right after I posted on here. Sorry about that.

Anyway, just to note for others who may have a similar issue here, 1.9.13-6~eugenesan~natty2 (from: [http://ppa.launchpad.net/eugenesan/ppa/ubuntu/](http://ppa.launchpad.net/eugenesan/ppa/ubuntu/) natty/main) does not seem to work at all, causing the above error. 

So while that it a great PPA, if you have that repo, I suggest downgrading to 1.9.13-5 (from: [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe), and then putting a hold on that particular package, so as to not have it just auto-update to the faulty package again. 

You can put a hold on a package via: echo "startupmanager hold" | sudo dpkg --set-selections .

---

### Post by thaak on 2011-10-24
Apparently startupmanager is not being actively maintained anymore. The developer recommends using the one bellow. Just for anyone else trying to sort out problems.

```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

```

---

### Post by inameiname on 2011-10-24
> **thaak said:**
> Apparently startupmanager is not being actively maintained anymore. The developer recommends using the one bellow. Just for anyone else trying to sort out problems.

```

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

```


Thanks for the info. I was not aware of that.

---

