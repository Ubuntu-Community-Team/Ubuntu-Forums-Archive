---
title: "Vuze crashes on opening any new torrent"
date: 2009-10-19
forum: General Help
---

### Post by Irishpolyglot on 2009-10-19
I am on 9.04 with Vuze 3.1.1.0 (I tried the latest version of Vuze but it starts up and then doesn't work; 3.1.1.0 is the only version permitted by default in Synaptic anyway).
I don't remember doing anything that could lead to this (I wasn't playing around in Vuze settings), other than accepting Ubuntu's usual updates. There is a torrent that I already had opened a week ago that downloads fine as soon as the program opens. However, any time I add *any* new torrent, the screen comes up to confirm and once I click on OK, Vuze greys out and remains that way for a long time and I have to kill the application. When I go back in (only after a reboot, since killing it leaves some other application connected to it open or whatever) that torrent wasn't added. So other than finishing the current torrent download, Vuze is currently useless.
I'd rather not use other torrent programs, but I have to for the moment. Any ideas on how to get around this?
Thanks!

---

### Post by gavshouse on 2009-10-19
> **Irishpolyglot said:**
> I am on 9.04 with Vuze 3.1.1.0 (I tried the latest version of Vuze but it starts up and then doesn't work; 3.1.1.0 is the only version permitted by default in Synaptic anyway).
I don't remember doing anything that could lead to this (I wasn't playing around in Vuze settings), other than accepting Ubuntu's usual updates. There is a torrent that I already had opened a week ago that downloads fine as soon as the program opens. However, any time I add *any* new torrent, the screen comes up to confirm and once I click on OK, Vuze greys out and remains that way for a long time and I have to kill the application. When I go back in (only after a reboot, since killing it leaves some other application connected to it open or whatever) that torrent wasn't added. So other than finishing the current torrent download, Vuze is currently useless.
I'd rather not use other torrent programs, but I have to for the moment. Any ideas on how to get around this?
Thanks!

same problem i noticed it after the update but i just tried today and its fine dont think ive done a update i have re-installed and restart since id try that mate

```
sudo apt-get remove vuze
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get install vuze
```

then reboot try again

---

### Post by Irishpolyglot on 2009-10-19
Cheers, that's done it :) I had already uninstalled and reinstalled it, but through Synaptic and without the autoclean/clean options. It didn't recognise vuze for installation, so I had to do the last part through Synaptic once again, but after a reboot it's all good now!

---

### Post by gavshouse on 2009-10-20
> **Irishpolyglot said:**
> Cheers, that's done it :) I had already uninstalled and reinstalled it, but through Synaptic and without the autoclean/clean options. It didn't recognise vuze for installation, so I had to do the last part through Synaptic once again, but after a reboot it's all good now!

yeah sorry its sudo apt-get install vuze silly me ive edited now just incase anyone else has this problem, gd luck anyway hope it dont happen again

---

