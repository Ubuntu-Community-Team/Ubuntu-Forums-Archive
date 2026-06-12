---
title: "Problem with ubuntu 11.10"
date: 2012-02-11
forum: General Help
---

### Post by khaj_vah on 2012-02-11
Hello people,
I have a problem with my ubuntu 11.10. I took a screenshot of a wondow.
That is how it looks like. Last thing i remember i did was,updating it, and something went wrong and now update manager says:

"Not all updates can be installed", and only few updates i can install. When i click on description of an update, it says: "This update does not come from a source that supports changelogs.".

Another problem, which i think is connected with this: After i do apt-get update, it says : 

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0"

P.S. if i change the theme from Ambiance, windows look OK.

---

### Post by duanedesign on 2012-02-11
> "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0"

Looks like you have a PPA that needs its public signature key.

To fix this open a Terminal and run the following command to download the key:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
```

While in the Terminal run the commands:

```
sudo apt-get update

sudo apt-get install -f 

sudo apt-get upgrade
```

If you get any errors when you run these please post the errors.

---

### Post by khaj_vah on 2012-02-11
nvm i solved it somehow

---

