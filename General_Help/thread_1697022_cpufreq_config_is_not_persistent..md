---
title: "cpufreq config is not persistent."
date: 2011-02-28
forum: General Help
---

### Post by dvdmchl on 2011-02-28
Have problem to configure cpufreq.
I want to use only two governors ondemand and powersaving.

Atm I have in /etc/rc.local those lines:
```
cpufreq-set -c 0 --min 800mhz --max 2.8ghz
cpufreq-set -c 1 --min 800mhz --max 2.8ghz
cpufreq-set -c 0 -g ondemand
cpufreq-set -c 1 -g ondemand

```

That works fine for few minutes. Then governor is changing to performance. When switching back to ondemand the frequency range is 2.8ghz-2.8ghz. So I need to manually call rc.local to fix it up.

How can I configure cpufreq permanently?

---

### Post by dcstar on 2011-03-01
> **dvdmchl said:**
> Have problem to configure cpufreq.
I want to use only two governors ondemand and powersaving.

Atm I have in /etc/rc.local those lines:
```
cpufreq-set -c 0 --min 800mhz --max 2.8ghz
cpufreq-set -c 1 --min 800mhz --max 2.8ghz
cpufreq-set -c 0 -g ondemand
cpufreq-set -c 1 -g ondemand

```

That works fine for few minutes. Then governor is changing to performance. When switching back to ondemand the frequency range is 2.8ghz-2.8ghz. So I need to manually call rc.local to fix it up.

How can I configure cpufreq permanently?

Install the **powernowd** package and use that.

---

### Post by dvdmchl on 2011-03-01
It's working now.
Was necessary to edit /etc/default/cpufreqd
```
CPUFREQ_CPU_MODULE="speedstep-centrino"
```
viz [http://ubuntuforums.org/showthread.php?t=248867]("http://ubuntuforums.org/showthread.php?t=248867")

Then configure /etc/cpufreqd.conf, that one is self explained.

Finally restart the service.
```
sudo service cpufreqd restart
```

Works like a charm now...

```
$ cpufreq-info --stats
2801000:42631, 2800000:2418, 2134000:300833, 1600000:84233, 800000:1031071  (9529)

```

---

