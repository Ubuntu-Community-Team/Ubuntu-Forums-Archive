---
title: "Network manager and external drives not working."
date: 2010-02-25
forum: General Help
---

### Post by abhishek198 on 2010-02-25
Hi,
I executed command to change folder permissions to 777 ..
but missed out "." while executing it.
I know this might sound lame .. but i was also using sudo while executing the command. ..

Ended up executing the following command ..
sudo chmod 0777 /

Now my n/w manager is not working .. and external drives are not getting detected.

Any clue how can i recover from the situation.


Regards
Abhishek Jain

---

### Post by nimrodwebdesign on 2010-02-25
Wow! :shock:


If you didn't use the [FONT="Courier New"]-R[/FONT] option in the command (to make it recursive through the whole directory structure), then you might be ok.


Try this:
```

# Set everything back to the common settings
sudo chmod 755 /

# Allow anyone access to the tmp folder
sudo chmod 777 /tmp

# ...but only file owners can delete files
sudo chmod +t /tmp

# limit access to root and lost+found folders
sudo chmod 700 /lost+found
sudo chmod 700 /root

# Set appropriate acces to proc folder
sudo chmod 555 /proc
```


The above will set you back to how my system is. The only thing is, I'm not sure how you will have effected symbolically linked files and folders. The above might be enough though.


Colin :)

---

