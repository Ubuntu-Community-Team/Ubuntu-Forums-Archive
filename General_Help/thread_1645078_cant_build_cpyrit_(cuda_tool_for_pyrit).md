---
title: "cant build cpyrit (cuda tool for pyrit)"
date: 2010-12-14
forum: General Help
---

### Post by Mikkel_ on 2010-12-14
So here i am just finished installing pyrit with quite alot of hassle and i want to get cuda support via cpyrit. only problem is the compiler pulling blanks all the time and i have no clue on where to find the library it wants.

i downloaded cuda and installed it via the script from nvidia.. to default libraries (just hit enter all the way through).. no problems there it seems.

after that i ran
```
sudo python setup.py build
```and got this result:

```
svn: '.' is not a working copy
running build
running build_ext
Skipping rebuild of Nvidia CUDA kernel ...
Building modules...
building 'cpyrit._cpyrit_cuda' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/local/cuda/include -I/usr/include/python2.6 -c _cpyrit_cuda.c -o build/temp.linux-i686-2.6/_cpyrit_cuda.o -DVERSION="0.3.0"
gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions build/temp.linux-i686-2.6/_cpyrit_cuda.o -lssl -lcuda -lz -o build/lib.linux-i686-2.6/cpyrit/_cpyrit_cuda.so
/usr/bin/ld: cannot find -lcuda
collect2: ld returned 1 exit status
```i gather the following from the README file..

```
By default, setup.py looks into '/usr/local/cuda' and '/opt/cuda' to find the
CUDA-headers and the compiler. Modify setup.py if you have those installed
elsewhere.

```my question is this where do i find my cuda-headers and compiler dirs to put into my setup.py?

cuda was installed into /usr/local/cuda
libs are in /usr/lib/nvidia-current/
as far as i can tell...

could you please educate an apt using newbie?  :confused:

EDIT: 

```
ld -l cuda
ld: cannot find -lcuda
```so i have to update ld to find the lib?

EDIT2: so i finally got my head around it and as it turns out it was fixed by creating a symlink in every lib directory i could think of... dont know which one is the right one though

---

### Post by krolikbunny on 2011-01-09
Hi i have the same error, Can you pls give me a hand to solve this problem

---

### Post by Hyprkookeez on 2011-01-13
```
sudo ln -s /usr/lib/nvidia-current/libcuda.so /usr/lib/libcuda.so
```

fixed it for me.

---

### Post by krolikbunny on 2011-01-15
THX it worked

---

### Post by urinophoria on 2012-03-18
> **Hyprkookeez said:**
> ```
sudo ln -s /usr/lib/nvidia-current/libcuda.so /usr/lib/libcuda.so
```

fixed it for me.

You sir, are my hero...

3 days of fighting this on an an asus u30SD...  got bumblebee installed, got cuda installed, got pyrit installed, then spent two and a half days on this.

you had the ONE post that finished sudo python setup.py build for me.

I owe you a beer

---

