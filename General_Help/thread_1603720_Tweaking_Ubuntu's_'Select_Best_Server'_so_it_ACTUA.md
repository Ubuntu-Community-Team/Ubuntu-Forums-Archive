---
title: "Tweaking Ubuntu's 'Select Best Server' so it ACTUALLY WORKS"
date: 2010-10-23
forum: General Help
---

### Post by Jebtrix on 2010-10-23
Lately I've been having super weak download speeds from the repositories (150-300KB/s on 20Mbit service). Using Ubuntu's [Select Best Server] never gives me the fastest server. Its always a toss up if the 'Best Server' will be marginally faster, the same, or even slower. After some tweaking it finally gave me a true fast server (2.6MB/s). The results are consistent so I thought I'd share it (got the same server 5 times in a row!).

What I basically did was disable the pinging of servers since its such a poor metric for ***throughput*** and force all mirrors to the perform download test. Obviously the testing takes longer, about 10mins but the result is worth it. First time I played with python but it gets the job done :P

gksudo gedit /usr/share/pyshared/softwareproperties/MirrorTest.py

Change:
```
    def run_full_test(self):
        # Determinate the 5 top ping servers
        results_ping = self.run_ping_test(max=5, borders=(0, 0.5), mod=(0,7))
        # Add two random mirrors to the download test
        size = len(self.mirrors)
        if size > 2:
            results_ping.append([0, 0, self.mirrors[random.randint(1, size-1)]])
            results_ping.append([0, 0, self.mirrors[random.randint(1, size-1)]])
```
To:
```
    def run_full_test(self):
        # Determinate the 5 top ping servers
        #results_ping = self.run_ping_test(max=5, borders=(0, 0.5), mod=(0,7))
        # Add two random mirrors to the download test
        #size = len(self.mirrors)
        #if size > 2:
        #    results_ping.append([0, 0, self.mirrors[random.randint(1, size-1)]])
        #    results_ping.append([0, 0, self.mirrors[random.randint(1, size-1)]])

        results_ping = []
	mirrors = self.mirrors	
	for m in mirrors:
    	    results_ping.append([0, 0, m])
```

To see some detailed output of download stats launch it in terminal:

gksudo /usr/bin/software-properties-gtk

---

