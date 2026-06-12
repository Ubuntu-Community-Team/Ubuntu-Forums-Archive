---
title: "sudo append not working"
date: 2012-04-27
forum: General Help
---

### Post by PGScooter on 2012-04-27
The following works fine for me:
log in as sudo su and then run
echo "deb [http://cran.mirrors.hoobly.com/bin/linux/ubuntu](http://cran.mirrors.hoobly.com/bin/linux/ubuntu) precise/" >> /etc/apt/sources.list

but when I try to do
sudo echo "deb [http://cran.mirrors.hoobly.com/bin/linux/ubuntu](http://cran.mirrors.hoobly.com/bin/linux/ubuntu) precise/" >> /etc/apt/sources.list

I get an error
"bash: /etc/apt/sources.list: Permission denied"

Is there anyway around this other than changing the file permissions, which I don't want to mess with?

---

### Post by gordintoronto on 2012-04-28
Who owns sources.list on your system?

Another approach is:
gksudo gedit /etc/apt/sources.list

---

### Post by bodhi.zazen on 2012-04-28
> **PGScooter said:**
> The following works fine for me:
log in as sudo su and then run
echo "deb [http://cran.mirrors.hoobly.com/bin/linux/ubuntu](http://cran.mirrors.hoobly.com/bin/linux/ubuntu) precise/" >> /etc/apt/sources.list

but when I try to do
sudo echo "deb [http://cran.mirrors.hoobly.com/bin/linux/ubuntu](http://cran.mirrors.hoobly.com/bin/linux/ubuntu) precise/" >> /etc/apt/sources.list

I get an error
"bash: /etc/apt/sources.list: Permission denied"

Is there anyway around this other than changing the file permissions, which I don't want to mess with?

Lots of options

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

If you want to re-direct output with sudo, use tee

```
echo "foo" | sudo tee >> output.file
```

or just become root

```
sudo -i
```

or edit

```
sudo -e /path/to/file_to_edit
```

---

### Post by PGScooter on 2012-05-01
Thank you for the replies.
I tried to do the following but it doesn't work:
```
echo "deb http://cran.mirrors.hoobly.com/bin/linux/ubuntu precise/" | sudo tee >> /etc/apt/sources.list
```

The reason I want to do this is because I want to put this in a bash script. I can I become root temporarily in a bash script?

Thanks

---

### Post by bodhi.zazen on 2012-05-01
> **PGScooter said:**
> Thank you for the replies.
I tried to do the following but it doesn't work:
```
echo "deb http://cran.mirrors.hoobly.com/bin/linux/ubuntu precise/" | sudo tee >> /etc/apt/sources.list
```

The reason I want to do this is because I want to put this in a bash script. I can I become root temporarily in a bash script?

Thanks

Why does that not work ?

You can either use sudo or run the script as root.

---

### Post by PGScooter on 2012-05-02
I get the same error as when I tried to run my original command:
```
bash: /etc/apt/sources.list: Permission denied

```

If I login to root by sudo su and then run the command without sudo then it's fine.

---

### Post by bodhi.zazen on 2012-05-02
My mistake

```
echo "deb http://cran.mirrors.hoobly.com/bin/linux/ubuntu precise/" | sudo tee -a /etc/apt/sources.list
```

---

### Post by PGScooter on 2012-05-04
> **bodhi.zazen said:**
> My mistake

```
echo "deb http://cran.mirrors.hoobly.com/bin/linux/ubuntu precise/" | sudo tee -a /etc/apt/sources.list
```

Cool, thank you bodhi.zazen

---

