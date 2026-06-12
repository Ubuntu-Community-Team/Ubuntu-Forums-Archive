---
title: "Update Manager Help"
date: 2009-07-26
forum: General Help
---

### Post by kyle2595 on 2009-07-26
When I go to the Update Manager and click "Check" it gives me an error message

"W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783"

It still shows me all of the available updates and still lets me download them, I was just wondering what it means and if there was any thing that I could do to fix it.

---

### Post by RedSingularity on 2009-07-26
Right click [here]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x79633A6C64DE9539") and _save link as._  Download the key to your desktop.  Then in system>admin>software sources, click the authentication tab.  Then click "import key file".  Select the file you just saved to desktop.

---

### Post by kyle2595 on 2009-07-26
It still gives me the same error message. Thanks for the attempt though.

---

### Post by RedSingularity on 2009-07-26
Did you see the key added to your authentication list?

---

### Post by plucky on 2009-07-26
> **kyle2595 said:**
> When I go to the Update Manager and click "Check" it gives me an error message

"W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783"

It still shows me all of the available updates and still lets me download them, I was just wondering what it means and if there was any thing that I could do to fix it.

See this [link](https://help.ubuntu.com/community/Medibuntu) for adding the Medibuntu Repository.

To add the GPG key ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

or

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


One of these methods should work

Good Luck

---

### Post by drs305 on 2009-07-26
Or the ever popular install-and-get-keyring-all-in-one-command answer for any release:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

```

From:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Or the short, specific answer:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2EBC26B60C5A2783

```

---

### Post by kyle2595 on 2009-07-27
Thank you all so much, it worked!

---

