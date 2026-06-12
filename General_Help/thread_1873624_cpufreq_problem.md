---
title: "cpufreq problem"
date: 2011-11-01
forum: General Help
---

### Post by csarcom on 2011-11-01
i have a quadcore CPU, when i use command:

sudo cpufreq-set -g performance

its only change CPU0 frequency. there is a command to set governors to all CPUs in the same time?

---

### Post by 3Miro on 2011-11-01
> **csarcom said:**
> i have a quadcore CPU, when i use command:

sudo cpufreq-set -g performance

its only change CPU0 frequency. there is a command to set governors to all CPUs in the same time?

You need to use:
```
sudo cpufreq-set -g performance -c 0
sudo cpufreq-set -g performance -c 1
sudo cpufreq-set -g performance -c 2
sudo cpufreq-set -g performance -c 3
```

Basically -c selects one of the CPUs that you have. You can make this into a bash script. Make a text file with:

```

#!/bin/bash
sudo cpufreq-set -g performance -c 0
sudo cpufreq-set -g performance -c 1
sudo cpufreq-set -g performance -c 2
sudo cpufreq-set -g performance -c 3
```

Then you can call the text file with:

```
sudo sh name_of_file
```

---

