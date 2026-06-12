---
title: "Can't get flash player to install"
date: 2009-11-04
forum: General Help
---

### Post by what, what? on 2009-11-04
I downloaded the .deb file from the adobe website and I keep getting this message: 
" Error: Dependency is not satisfiable: libnspr4-dev "
Can anybody help me out with this?

---

### Post by wojox on 2009-11-04
Open a terminal and run:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by what, what? on 2009-11-04
> **wojox said:**
> Open a terminal and run:

```
sudo apt-get install flashplugin-nonfree
```

Says it couldnt find it..

---

### Post by what, what? on 2009-11-04
So yeah....

---

### Post by wojox on 2009-11-04
Did you copy and paste that. It needs the **install** part.

---

### Post by what, what? on 2009-11-04
> **wojox said:**
> Did you copy and paste that. It needs the **install** part.

I guess i missed a part of it. My bad. It's working now.

---

### Post by wojox on 2009-11-04
10-4

---

### Post by guriinii on 2009-11-04
Open a terminal and run:

```
sudo apt-get ubuntu-restricted-extras
```That may do it. 
To check type *about:plugins* in the Firefox browser bar, there should be a list of stuff including Flash.

---

