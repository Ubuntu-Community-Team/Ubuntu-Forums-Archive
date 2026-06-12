---
title: "Synaptic Package Manager crashes (Ubuntu 11.10)"
date: 2011-12-19
forum: General Help
---

### Post by ruben2020 on 2011-12-19
Hello all,

I'm using Ubuntu 11.10, Gnome3 Shell, Synaptic Package Manager. On opening the Synaptic Package Manager, it crashes immediately after the authentication screen.

Then, I tried to launch it by command line, and after the authentication screen, it crashes with the following:

```
[FONT=Courier New][COLOR=Black]$ synaptic-pkexec 
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted[/COLOR][/FONT]
```

Please help.

---

### Post by philinux on 2011-12-19
Could it be this. [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/807771](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/807771)

---

### Post by thaelim on 2011-12-19
Sounds about right... my solution - ```
sudo synaptic
``` instead. Or just use apt-get :)

---

### Post by ruben2020 on 2011-12-19
Thanks, Phil. Running the following, allows Synaptic to start normally.

```
gsettings set org.gnome.desktop.interface toolkit-accessibility false
```

---

