---
title: "Thunderbird won't launch after upgrade"
date: 2009-11-06
forum: General Help
---

### Post by kcredden on 2009-11-06
Hey folks: This morn, I was alerted to a set of security patches, which I installed. Now Thunderbird won't launch. The effect is exactly what was reported here: [http://ubuntuforums.org/showthread.php?t=599452](http://ubuntuforums.org/showthread.php?t=599452)

I tried the solutions, but libstdc++6 - The GNU Standard C++ Library v3 is already installed according to Synaptic. 

I tried 'thunderbird' inside a terminal and got: 

$kcredden@cable5-207:~$ thunderbird
/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Can you help? 

- Kc

---

### Post by kcredden on 2009-11-08
Ok folks: No one came up with a solution so I got one of my own. Install libstdc++5 1:3.3.6.17ubuntu1 via Synaptic and it works. No idea why I have v6, and it needs 5 or so. 

- Kc

---

