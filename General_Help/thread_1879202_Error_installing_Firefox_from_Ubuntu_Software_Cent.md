---
title: "Error installing Firefox from Ubuntu Software Center"
date: 2011-11-11
forum: General Help
---

### Post by Tornikee on 2011-11-11
Hello,

I tried to install Firefox from the USS, although got these two messages:

(1) 'Failed to download package files. Check your internet connection' (screenshot: [https://lh3.googleusercontent.com/-29US03DyGG0/Trz4c05bQdI/AAAAAAAADAk/1QhFe9cw9Pc/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A25%25253A25.png](https://lh3.googleusercontent.com/-29US03DyGG0/Trz4c05bQdI/AAAAAAAADAk/1QhFe9cw9Pc/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A25%25253A25.png))
(2) 'The action would require the installation of packages from not authenticated sources'. Details: 'firefox firefox-globalmenu' (screenshot: [https://lh5.googleusercontent.com/-7oh_e0K2v2o/Trz4cziddCI/AAAAAAAADAg/1w7Zvhxl4Yc/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A25%25253A30.png](https://lh5.googleusercontent.com/-7oh_e0K2v2o/Trz4cziddCI/AAAAAAAADAg/1w7Zvhxl4Yc/s0/Screenshot%252520at%2525202011-11-11%25252014%25253A25%25253A30.png))

Guess this has something to do w/ software sources - I might have removed some instance that is needed for this installation - but how can I correct this?

Ubuntu 11.10

---

### Post by sikander3786 on 2011-11-11
Yeah, perhaps something to do with the software sources or repository index etc.

Please get to a Terminal (search the Dash after pressing <Super> key) and run these commands:

```
sudo apt-get update
sudo apt-get install firefox
```

If it still returns an error, please post the complete outputs of above commands and also of this one:

```
cat /etc/apt/sources.list
```

---

### Post by An Sanct on 2011-11-11
Maybe you deleted the thing from software sources.

Try to reinstall via PPA

```
[FONT=inherit]
sudo add-apt-repository ppa:chrisccoulson/ppa[/FONT]
[FONT=inherit]sudo apt-get update[/FONT]
[FONT=inherit]sudo apt-get upgrade[/FONT]
[FONT=inherit]sudo apt-get install firefox-globalmenu[/FONT]
```

This should automagically add the security keys and everything.

---

### Post by Tornikee on 2011-11-11
> **sikander3786 said:**
> Yeah, perhaps something to do with the software sources or repository index etc.

Please get to a Terminal (search the Dash after pressing <Super> key) and run these commands:

```
sudo apt-get update
sudo apt-get install firefox
```

If it still returns an error, please post the complete outputs of above commands and also of this one:

```
cat /etc/apt/sources.list
```

Solved using your suggestion. Thanks a lot.

---

