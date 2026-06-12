---
title: "How to install Nvidia drivers on USB installation for general use?"
date: 2012-03-21
forum: General Help
---

### Post by lucusoid on 2012-03-21
Hi everyone!

I am using Ubuntu since Hardy and it never ceases to amaze me... Whatever new distro I try out I find myself comming back again.
One thing I find of great interrest is its portability. So I installed the whole system to a Mushkin pro 64GB and it is lightning fast.
With the default installation everything works on whatever computer I am in front of. 

To my question now... 
When installing Nvidia drivers in such a system, there is a problem with glx extensions on computers without an Nvidia card present.
I know there is always the update-alternatives method of setting who provides glx, but it is kind of unconvenient to just restart after setting this.
So one approach I could think of is to create a startup script wich states

#!/bin/bash

if [[ `lspci |grep VGA` == *nVidia* ]]
then
  echo "Nvidia devices found"
  [COLOR="Red"]set update-alternatives to nvidia glx[/COLOR]
else
  echo "Nvidia devices not found"
  [COLOR="Red"]set update-alternatives to mesa glx[/COLOR]
fi

and then add this script to boot with update-rc.d

Any idea on how to formulate this script?

---

### Post by nothingspecial on 2012-03-23
*Thread moved to **General Help**.*

---

