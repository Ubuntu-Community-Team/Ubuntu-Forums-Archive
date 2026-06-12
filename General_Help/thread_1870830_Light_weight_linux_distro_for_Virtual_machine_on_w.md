---
title: "Light weight linux distro for Virtual machine on win 7  - 64 bit"
date: 2011-10-27
forum: General Help
---

### Post by rishi_singh on 2011-10-27
Hi Guys ! 

I need your help to decide which **lightweight, gui based **linux distro to put into oracle virtualbox which i have installed inside windows 7 - 64 bit.

My **main requirement** is that i should be able to access internet from the linux distro which will be running inside the VM. I already have ubuntu 11.1 on dual boot which seems to be okay as of now. I did have some problems with wifi before. so, I wanted to know the distro in which my wifi will work when i put it inside the VM.

**why am i doing this ? **I want another distro of linux which i can use directly, without having to turn off windows. 

All suggestions are welcome.

---

### Post by dfarrell07 on 2011-10-28
What kind of hardware specs are you working with? If you want really light weight, go for Xubuntu ([http://www.xubuntu.org/](http://www.xubuntu.org/)) or Puppy Linux ([http://bit.ly/vHV2gO](http://bit.ly/vHV2gO)).

---

### Post by Rodney9 on 2011-10-28
Try Lubuntu

---

### Post by rishi_singh on 2011-10-28
> **dfarrell07 said:**
> What kind of hardware specs are you working with? If you want really light weight, go for Xubuntu ([http://www.xubuntu.org/](http://www.xubuntu.org/) [IMG]http://ubuntuforums.org/data:image/gif;base64,R0lGODlhEQAQAOYAAIaoKaLLIq7bOqDJIJC2K4WnKd3xq5/HHbDdPKnUL6rWMqTOKKfSLaPMJabQKqzYNK3ZN/7+/YepKZe7Ofj68pW7KZ3EJoywKqXPKoywJunw18bldo+zJZzEHomsKo2tN4irKpvCL4+uOKDII5rBLJe6OrXfSaLLMYuuKpi7O8flet3nw5/III2xKI2yKpzELLLId+rw2YuvKo6zLI60K4eqKbjQeN/qw5O4Ka/bPNTgtL/RjrPeRKrVMdbtnqfCX6jDX4irKZa5NtjmtZO5LYiqKo+zKbjNfpOzPs3en4mrKZ3FHoquKrXcSp7GL7HcQY6uOcjXnq3OVJa8K8Deb5C0Kc3phYyvKo6zK4yxKq/QWqLLJZO5LpW7K57HIaXITKPGSJ/ILJrCKMPXj5i5P7HTVLDaPo2xJ7rQfpG2LbndV6PKNY6yKNjuoomtKv///wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAEAAG8ALAAAAAARABAAAAfOgG+CbxFJEwSIiYgpg4Q2Xz4GkpMGbVolg2NgViYInp8IPBs0gjcTKjkCqqurT1hvFGRUZhAAAFwQabZFEBAub2hSTQ8PtkQhthInxFkaQmoK0bZXErZO0QoXQGU9Cd624CTe3jI/awzoDOAAU10vYehMMTMYDvbgOBUASkb2bm9HKiwYaKvKAjFBbA30AAuJhQYNALTY0sACG1sQQQhagWJEgI8gQwaoMWjHGRYDUqpU6UXCoAgwMnQ4QLPmgSUcRDSKEOVDgZ9Af0J5EwgAOw==[/IMG] ) or Puppy Linux ([http://bit.ly/vHV2gO](http://bit.ly/vHV2gO) [IMG]http://ubuntuforums.org/data:image/gif;base64,R0lGODlhEQAQAOYAAIaoKaLLIq7bOqDJIJC2K4WnKd3xq5/HHbDdPKnUL6rWMqTOKKfSLaPMJabQKqzYNK3ZN/7+/YepKZe7Ofj68pW7KZ3EJoywKqXPKoywJunw18bldo+zJZzEHomsKo2tN4irKpvCL4+uOKDII5rBLJe6OrXfSaLLMYuuKpi7O8flet3nw5/III2xKI2yKpzELLLId+rw2YuvKo6zLI60K4eqKbjQeN/qw5O4Ka/bPNTgtL/RjrPeRKrVMdbtnqfCX6jDX4irKZa5NtjmtZO5LYiqKo+zKbjNfpOzPs3en4mrKZ3FHoquKrXcSp7GL7HcQY6uOcjXnq3OVJa8K8Deb5C0Kc3phYyvKo6zK4yxKq/QWqLLJZO5LpW7K57HIaXITKPGSJ/ILJrCKMPXj5i5P7HTVLDaPo2xJ7rQfpG2LbndV6PKNY6yKNjuoomtKv///wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAEAAG8ALAAAAAARABAAAAfOgG+CbxFJEwSIiYgpg4Q2Xz4GkpMGbVolg2NgViYInp8IPBs0gjcTKjkCqqurT1hvFGRUZhAAAFwQabZFEBAub2hSTQ8PtkQhthInxFkaQmoK0bZXErZO0QoXQGU9Cd624CTe3jI/awzoDOAAU10vYehMMTMYDvbgOBUASkb2bm9HKiwYaKvKAjFBbA30AAuJhQYNALTY0sACG1sQQQhagWJEgI8gQwaoMWjHGRYDUqpU6UXCoAgwMnQ4QLPmgSUcRDSKEOVDgZ9Af0J5EwgAOw==[/IMG] ).

Multicore intel processor, 6gb ram, onboard intel gpu. As you can see, my hardware specs are good, so thats not the reason for the lightweight part of the requirement. I wanted the distro installation to be small and fast(er  than ubuntu).

---

### Post by dfarrell07 on 2011-10-28
The main limiting factor for running something like Ubuntu 11.04 or 11.10 would be the onboard graphics. I imagine Unity and Windows would own those fairly quickly. Any of the above should work nicely. :)

---

### Post by shubham1 on 2011-10-28
> **rishi_singh said:**
> Multicore intel processor, 6gb ram, onboard intel gpu. As you can see, my hardware specs are good, so thats not the reason for the lightweight part of the requirement. I wanted the distro installation to be small and fast(er  than ubuntu).
puppy linux installs on ram see clearly fast

---

### Post by mörgæs on 2011-10-28
There are a lot of suggestions here:
[http://ubuntuforums.org/showthread.php?t=1842053](http://ubuntuforums.org/showthread.php?t=1842053)

---

### Post by rishi_singh on 2011-10-30
Is xubuntu related to ubuntu. My guess is that, if they are related, then i can hope that my wifi will work on xubuntu if it works on ubuntu too. The main things are lightweight, gui and working wifi.

---

### Post by cddt on 2011-10-30
For a lightweight distro which is also a Ubuntu variant, I recommend Lubuntu. I have installed this on a laptop dating from 2004, and it runs a lot faster than I expected.

---

### Post by Rodney9 on 2011-10-30
> **rishi_singh said:**
> Is xubuntu related to ubuntu. My guess is that, if they are related, then i can hope that my wifi will work on xubuntu if it works on ubuntu too. The main things are lightweight, gui and working wifi.

Yes X or L or K Ubuntu are all related and have the same base with a different window manager.

---

### Post by spcwingo on 2011-10-30
> **rishi_singh said:**
> Is xubuntu related to ubuntu. My guess is that, if they are related, then i can hope that my wifi will work on xubuntu if it works on ubuntu too. The main things are lightweight, gui and working wifi.

Vbox does not use your physical network interface unless you explicitly tell it to do so.  That being said, if you are connected to a network in Win you will be able to connect in your virtual machine.

---

### Post by coldraven on 2011-10-30
Ready made VMs here, take your pick :)
[http://virtualboxes.org/images/](http://virtualboxes.org/images/)

---

### Post by rishi_singh on 2011-10-30
Then, lubuntu it is.

---

### Post by rishi_singh on 2011-11-08
UPDATE:

tried installing lubuntu inside a virtual machine. Cannot. Please see the post below if you can.

[http://ubuntuforums.org/showthread.php?t=1877358](http://ubuntuforums.org/showthread.php?t=1877358)

---

### Post by aura7 on 2011-11-08
Try Damn Small Linux, I am sure that you will find nothing is  lighter than this.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by spcwingo on 2011-11-08
> **aura7 said:**
> Try Damn Small Linux, I am sure that you will find nothing is  lighter than this.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

DSL is no longer being actively developed.  Slitaz or Tinycore would be better choices.  ;)

---

