---
title: "Script: Howto have INSTALL accept default?"
date: 2010-06-07
forum: General Help
---

### Post by held7over on 2010-06-07
Ubuntu 10.04

My script stops and waits for user input on such things as installing acroread and jackd, etc. Is there a "switch" to the apt-get install command that will cause any suggested default the apt-get command happens to bump into to automatically be accept the default and not stop the script from running?

I have been looking at the "man" listing, but evidently I don't understand the write up well enough to realize which switch to use...

Thanks! :)

---

### Post by davidmohammed on 2010-06-07
try the -y switch (assume yes  to prompts)

i.e. apt-get -y install acroread

---

### Post by held7over on 2010-06-07
That's what I thought it would do, but I tried that already, however in the following apt-get install command, the script still stops on the acroread install. 

```
echo "Begin Install of Applications"
echo
echo 'Step 1' >> ~/install_log
echo "Step 1" # These things I want to install first for different reasons--

**sudo apt-get -y install firestarter app-install-data-medibuntu apport-hooks-medibuntu acroread acroread-fonts thunderbird**
echo 'Finished' >> ~/install_log
```

---

### Post by davidmohammed on 2010-06-07
bizarre - I can't reproduce

is it because you are trying to install multiple apps on one line?

try separating each app with its own sudo apt-get -y install

does aptitude make any difference?

i.e.

sudo aptitude -y install acroread

---

