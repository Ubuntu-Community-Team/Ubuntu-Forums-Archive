---
title: "remove transmission-daemon from startup"
date: 2011-04-01
forum: General Help
---

### Post by d3v1150m471c on 2011-04-01
I've tried the following in rc.local but it gets me nowhere:
```

TRANSMISSION_TIMING() {
                       for((a=0;a<=5;a++)); do
                       sleep 1 &
                       wait
                       [[ $(top -n1 | grep transmission) == *transmission* ]] && \
                       [[ $(date +%H) -ge 5 ]] && [[ $(date +%H) -lt 23 ]] && /etc/init.d/transmission-daemon stop
                       done
                      }

TRANSMISSION_TIMING &

``````

TRANSMISSION_TIMING() {
                       [[ $(top -n1 | grep transmission) == *transmission* ]] && \
                       [[ $(date +%H) -ge 5 ]] && [[ $(date +%H) -lt 23 ]] && /etc/init.d/transmission-daemon stop
                      }

TRANSMISSION_TIMING &

```nothing i do can keep this thing from launching, and apparently kill it either.

---

### Post by d3v1150m471c on 2011-04-01
...i always do this...
```

TRANSMISSION_TIMING() {
            /etc/init.d/transmission-daemon stop
            [[ $(date +%H) -lt 5 ]] && /etc/init.d/transmission-daemon start
                      }

TRANSMISSION_TIMING

```

^ works

---

