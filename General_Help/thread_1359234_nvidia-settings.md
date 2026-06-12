---
title: "nvidia-settings"
date: 2009-12-19
forum: General Help
---

### Post by HarshReality on 2009-12-19
OK, so Im in terminal and run nvidia-settings -q gpus.. I get both GPUs listed as so..
```

steven@steven-desktop:~$ nvidia-settings -q gpus

2 GPUs on steven-desktop:0

    [0] steven-desktop:0[gpu:0] (GeForce 9600 GSO)

    [1] steven-desktop:0[gpu:1] (GeForce 7025 / nForce 630a)

```

What I am trying to do is get a command to display only a specified GPU..

nvidia-settings -q gpus | grep etc for example.. but nothing I am trying is working here.

---

