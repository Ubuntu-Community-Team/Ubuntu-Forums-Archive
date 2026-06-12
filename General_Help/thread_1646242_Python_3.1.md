---
title: "Python 3.1"
date: 2010-12-15
forum: General Help
---

### Post by ki4jgt on 2010-12-15
Just installed Python 3 but every time I enter Python at the terminal I get 2.6. How do I use 3.1

---

### Post by Cheesehead on 2010-12-15
```
spambot:~$ python     # Launches system default python, currently 2.6

spambot:~$ python3    # Launches python3
```

---

### Post by WorMzy on 2010-12-15
/usr/bin/python is merely a symbolic link to /usr/bin/python2.6. To launch python3, you should run
```
python3
```

To create python3 scripts, you should use the shebang
```
#!/usr/bin/python3
```
or
```
#!/usr/bin/env python3
```

---

