---
title: "How to find if a particular software is installed."
date: 2012-06-21
forum: General Help
---

### Post by swavijay on 2012-06-21
Hi Experts,

I'm writing a python script which downloads latest source from git, generates a build and run some automated test case. I'm running that on a ubuntu machine. As a pre-requisite i would need to have git and g++ complier to do that.

I wanted to write script in such a way that if git and g++ are not installed, I would like to get it installed and then proceed with my test.

so my requirement is to check if git and g++ are installed in ubuntu. is there a way to check if these softwares are installed in ubuntu? how do I confirm that.

I can run gig --version to find if git is installed but i'm trying to see a generic option which lists down the list of programs / softwares installed and that way i can check in that repository?

Please advice.

Thanks.
-Vijay

---

### Post by codemaniac on 2012-06-21
Use dpkg -l , if a package(sat git) is installed the below commandline would return you the details .

```
dpkg -l | awk '$1 ~ /^ii/ && $2 ~ /git/{print}'
```

---

