---
title: "HELP! Missing /usr/bin/python"
date: 2011-07-08
forum: General Help
---

### Post by qingkunl on 2011-07-08
Hello,
I accidentally delete the /usr/bin/python on my Ubuntu. And now I whenever I want to run python, it will complain bash: /usr/bin/python: No such file or directory
Does anyone know how to solve this?

Thanks,
Qingkun

---

### Post by wojox on 2011-07-08
You didn't delete python2.7 did you? Try linking it:

```
sudo ln -s /usr/bin/python2.7 /usr/bin/python
```

---

### Post by qingkunl on 2011-07-08
Great! Thanks so much.

---

### Post by qingkunl on 2011-07-08
Can I ask you another question? That is how to change the default directory to find python, like change to /usr/local/bin/python, instead of /usr/bin/python.

Thanks

---

### Post by wojox on 2011-07-08
This may work, if not we can change it back:

```
sudo rm /usr/bin/python
```

```
sudo ln -s /usr/bin/python2.7 /usr/local/bin/python
```

---

