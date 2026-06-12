---
title: "Frozen Update Manager"
date: 2012-05-17
forum: General Help
---

### Post by Nosophorus on 2012-05-17
Hi!

I'm using Ubuntu 12.04 LTS with XFCE Desktop Environment (but I also have Unity and GNOME3 installed in the case I need them). I added the Medibuntu repositories and did the usual updates. But I realized that, for the kind of things I do on my computer, I don't need Medibuntu and, then, I used the Software Channels to remove it (I just unmarked Medibuntu at Software Channels list).

But, since then, every time there is an update and I launch the Update Manager, when I click the "Install Updates" button, the Update Manager gets frozen for, at least, 5 minutes (!) and its screen is not responsive for all that time. This problem did not happen before adding/installing Medibuntu.

I installed Medibuntu according to the [instructions available at medibuntu.org]("http://medibuntu.org/repository.php"):

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Then I did:

```
sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
```

What should I do to fix the frozen Update Manager?

Thanks!

---

### Post by plucky on 2012-05-18
> **Nosophorus said:**
> Hi!

I'm using Ubuntu 12.04 LTS with XFCE Desktop Environment (but I also have Unity and GNOME3 installed in the case I need them). I added the Medibuntu repositories and did the usual updates. But I realized that, for the kind of things I do on my computer, I don't need Medibuntu and, then, I used the Software Channels to remove it (I just unmarked Medibuntu at Software Channels list).

But, since then, every time there is an update and I launch the Update Manager, when I click the "Install Updates" button, the Update Manager gets frozen for, at least, 5 minutes (!) and its screen is not responsive for all that time. This problem did not happen before adding/installing Medibuntu.

I installed Medibuntu according to the [instructions available at medibuntu.org]("http://medibuntu.org/repository.php"):

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Then I did:

```
sudo apt-get install app-install-data-medibuntu apport-hooks-medibuntu
```

What should I do to fix the frozen Update Manager?

Thanks!

Post output from a terminal for ```
sudo apt-get update && sudo apt-get upgrade
```

Good Luck

---

