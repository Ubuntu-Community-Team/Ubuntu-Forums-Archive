---
title: "Install package from different distro"
date: 2011-12-03
forum: General Help
---

### Post by Desargues on 2011-12-03
Hello,

I would like to install gfortran 4.6 on my 10.04 distribution, but it is not available in the synaptic package manager. Is it possible to use the gfortran 4.6 deb file that is available for the current release of ubuntu, or is a manual install the only solution?

---

### Post by dcstar on 2011-12-04
> **Desargues said:**
> Hello,

I would like to install gfortran 4.6 on my 10.04 distribution, but it is not available in the synaptic package manager. Is it possible to use the gfortran 4.6 deb file that is available for the current release of ubuntu, or is a manual install the only solution?

Download it and try to install it with the gdebi tool, it will soon tell you if it installs ok or has dependency issues.

I have installed many packages from subsequent releases without any issues **as long** as the dependencies are satisfied.

---

### Post by cap10Ibraim on 2011-12-04
installing it from the terminal will show you important output

---

### Post by raja.genupula on 2011-12-04
1...first get that package from the ubuntu packages 
2...try to install with the 

sudo dpkg -i <filename.deb>

3...if you faced any dependencies issues open synaptic and look for them 
or
apt-get install -f 

4...then try to install again.

all the best

---

