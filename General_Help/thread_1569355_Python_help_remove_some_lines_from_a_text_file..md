---
title: "Python help: remove some lines from a text file."
date: 2010-09-06
forum: General Help
---

### Post by cgroza on 2010-09-06
Hello, I am creating my own address book Python program and I want to create a function that removes some specified  entries. The code looks like this now. 

```
def remove():
    delentry= raw_input('Enter the entry name to delete: ')
    dafi = open('/home/cgroza/.contacts','r')
            
    for line in dafi:
        if delentry in line:
            dafi = open('/home/cgroza/.contacts','w')
            dafi.write("                       ")
        print 'Entry deleted.'
        raw_input('Press <enter> to continue.This will clear the text.')
        os.system('clear')
        choicer()
```
Well, it removes all my entries, so if i run this i will loose all my address book entries. But i want to delete just the one i want. Thanks. I'm a beginner.

---

### Post by cgroza on 2010-09-06
any one?

---

