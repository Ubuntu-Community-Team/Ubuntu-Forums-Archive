---
title: "Python. Need advice."
date: 2010-09-07
forum: General Help
---

### Post by cgroza on 2010-09-07
Hello, I have this Python address book and i want to make it run on every computer. Now it will work only on my computer because a path is hard coded into the program. The path is /home/cgroza/....
Now for another user this path will not exist.  Please tell me how do i make the program write in any home directory, whatever its name is.Thank you. Here is the code.

```

#!/usr/bin/env python

import time
import os


def choose():
    choice = raw_input ('Enter:\n1 to Create an Entry\n2 to Search an Entry.\n3 to Remove Entry.\n4 to Display ALL\n5 to Import/Export\n6 to Destroy Data\n1/2/3/4/5/6: ')
    if choice == '1':
        create()

    elif choice == '2':
        read()          

    elif choice == '3':
        remover()

    elif choice == '4':
        showall()

    elif  choice == '5':
          os.system('clear')
          pick=raw_input('To import enter 1.\nTo export enter 2.: ')
          if pick == '1':
              importer()
          elif pick == '2':
              exporter()
          else:
              print('Invalid Command')
              time.sleep(3)
              os.system('clear')
              choose()


    elif choice == '6':
        destroy()


    elif choice == 'q':
        quit
        
    else:
        print('Invalid Command')
        time.sleep(3)
        os.system('clear')
        choose()
        

def create():
    name = raw_input('Enter the name: ')
    telnr= raw_input('Enter the phone number: ')
    address = raw_input('Enter the address: ')
    email = raw_input('Enter the email: ')
    dafi = open('/home/cgroza/.contacts','a')
    dafi.write(name +', '  + telnr + ', ' + address + ', '  + email)
    dafi.write('\n')
    dafi.close()
    print ('Entry saved')
    time.sleep(1)
    os.system('clear')
    choose()
    
                                                                                                               


def read():
    search=raw_input('Enter search criteria: ')
    print ("Stored data for " + search + " is: ")
    dafi = open('/home/cgroza/.contacts','r')
    for line in dafi:
        if search in line:
            print line
            dafi.close()
        raw_input('Press <enter> to continue.This will clear the results.')
        os.system('clear')
        choose()        
         
         
def remover():
    delentry = raw_input('Enter entry name to delete: ')
    fhi = open('/home/cgroza/.contacts', "r")
    fho = open('/home/cgroza/.tempcontacts2', "a")
    for line in fhi.readlines():
        if delentry not in line:
            fho.write(line)                   
    fhi.close()
    fho.close()     
    os.rename('/home/cgroza/.tempcontacts2','/home/cgroza/.contacts')
    os.system('clear')
    choose()     
         
         
         

def showall():
    dafi=open('/home/cgroza/.contacts','r')
    show = dafi.read()
    print show
    raw_input('Press <enter> to continue.This will clear the text.')
    os.system('clear')
    choose()


def exporter():
    path=raw_input('Enter the full path (including filanme): ')
    exportcmd = 'cp ~/.contacts '+path
    os.system(exportcmd)
    print ('Export Done to'+path)
    time.sleep(3)
    os.system('clear')
    choose()


def importer():
    path=raw_input('Enter the path to file (including filename): ')
    importcmd='cp '+path+' ~/.contacts'
    os.system(importcmd)
    print('Import Done')
    time.sleep(3)
    os.system('clear')
    choose()


def destroy():
    ask= raw_input('This will destroy your data! ARE YOU SURE?/y/n')
    if ask == 'y':
        dafi=open('/home/cgroza/.contacts','w')
        dafi.write('')
        print('Data was Destroyed!')
        time.sleep(3)
        os.system('clear')
        choose()
        
    elif ask == 'n':
        choose()

    else:
        print('Invalid Command')
        time.sleep(3)
        os.system('clear')
        destroy()

            
choose()

```

---

### Post by endotherm on 2010-09-07
well, this is not an entirely simple question, so you won't get all the info you want in one neat reply, but as for finding the home, in linux, your users home can be refered to by '$HOME' and in windows the userhome can be found with %USERPROFILES%. 
the trick with cross platform pathing, is to let the runtime (python interpreter) do the work. from the os lib you should be able to pull the path seperator for the running os, so you concatenate your paths together, or use os.path.join() to assemble it.


good luck

---

### Post by tgm4883 on 2010-09-07
Couple ways you could do it. You probably want to get the current user home directory with something like

```

import os
HOMEDIR = os.path.expanduser('~')
```

Then turn that into a contacts path variable that you could use elsewhere

```
CONTACT_PATH = HOMEDIR+"/.contacts"
```

Then in your code you would use this instead of '/home/cgroza/.contacts'. 

ie. Instead of 

```
dafi = open('/home/cgroza/.contacts','a')
```

you would use

```
dafi = open(CONTACT_PATH,'a')
```

---

### Post by tgm4883 on 2010-09-07
Also, take a look at this page which is what I was using with this. Apparently it works on Linux and Windows

[http://snipplr.com/view/7354/home-directory-crossos/](http://snipplr.com/view/7354/home-directory-crossos/)

---

### Post by cgroza on 2010-09-07
Thank you very much. You helped me a lot.

Just one more question. There is any module that copies a file from one place to another because i use 'cp' that is a Linux program so my application is not multi platform right now.

---

### Post by btindie on 2010-09-07
A simple Google of "[python copy file]("http://www.google.co.uk/search?q=python+copy+file")" would have answered your question.
 
Take a look at the Python docs [here]("http://docs.python.org/release/2.5.2/lib/module-shutil.html").

---

### Post by cgroza on 2010-09-07
Thanks...

---

