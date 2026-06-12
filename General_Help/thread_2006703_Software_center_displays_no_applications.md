---
title: "Software center displays no applications"
date: 2012-06-19
forum: General Help
---

### Post by jeddi00 on 2012-06-19
just installed lubuntu and went into synaptic got software center,etc,but whenever i open the center it displays canonical,provided by ubuntu and 3rd party software(or something like that) but if i search or click games,system,accesories etc it come up with nothing,i have my server thing set to main server but it still wont come up



thanks,jeddi00

---

### Post by cortman on 2012-06-19
> **jeddi00 said:**
> just installed lubuntu and went into synaptic got software center,etc,but whenever i open the center it displays canonical,provided by ubuntu and 3rd party software(or something like that) but if i search or click games,system,accesories etc it come up with nothing,i have my server thing set to main server but it still wont come up



thanks,jeddi00

Click the "Refresh" button in Synaptic, or run

```
sudo apt-get update
```

in a terminal. The software list needs to be updated after installation.

---

### Post by jeddi00 on 2012-06-20
> **cortman said:**
> Click the "Refresh" button in Synaptic


by that do you mean reload or something else?(beacuse ive already ran sudo apt-get update)

thanks for the reply

---

### Post by cortman on 2012-06-20
> **jeddi00 said:**
> by that do you mean reload or something else?(beacuse ive already ran sudo apt-get update)

thanks for the reply

There's a big button in Synaptic called "Refresh" with green circle arrows- click it. Could be you need to do that even if you ran sudo apt-get update.

---

