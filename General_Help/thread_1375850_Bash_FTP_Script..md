---
title: "Bash FTP Script."
date: 2010-01-08
forum: General Help
---

### Post by Chamillionaire2 on 2010-01-08
What's Up?

So, I'm making a script that includes some ftp usage, But so far, After it's finished doing the ftp commands, It won't carry out any more bash commands. Example.
```

echo Yo!
ftp -n -i <<_EOF_
open ftp.server.com
user user password
put contents.txt
close
bye
echo Go!
```

Once put into a script it _will_ execute "echo Yo!" But _not_ "echo Go!"

Anyone know why and how to get around this?

Thanks Bye.

---

### Post by snoop2048 on 2010-01-08
Does it do it if you put the commands in a different script and call it from this script?

I.e

echo test1

./ftp.bash

echo test2

If so, you could fork the call to the background. I.e

echo test1 
./ftp.bash &
echo test2

Try a few things out, see what you get. 

Si

---

### Post by Chamillionaire2 on 2010-01-08
> **snoop2048 said:**
> Does it do it if you put the commands in a different script and call it from this script?

I.e

echo test1

./ftp.bash

echo test2

If so, you could fork the call to the background. I.e

echo test1 
./ftp.bash &
echo test2

Try a few things out, see what you get. 

Si

Thanks for replying, But I get "bash: /home/zack/Desktop/ftp.txt: Permission denied" Is is possible to do this without changing the permissions?

---

### Post by snoop2048 on 2010-01-08
> **Chamillionaire2 said:**
> Thanks for replying, But I get "bash: /home/zack/Desktop/ftp.txt: Permission denied" Is is possible to do this without changing the permissions?

 Your script needs to be executable to run it - You cant get around that.

Have a look at chmod command.  

Just as an aside, you should call it ftp.sh or ftp.bash, its good practice. 

Si

---

### Post by Chamillionaire2 on 2010-01-08
> **snoop2048 said:**
> Your script needs to be executable to run it - You cant get around that.

Have a look at chmod command.  

Just as an aside, you should call it ftp.sh or ftp.bash, its good practice. 

Si

Really? Damn, Ow well thanks for your help :-)

---

### Post by snoop2048 on 2010-01-08
> **Chamillionaire2 said:**
> Really? Damn, Ow well thanks for your help :-)

Yes, really. 

All the wrapper script is doing is calling another script (ftp.bash), that has to be the same insofaras it needs a shell path on the first line, and needs to be executable by the user that runs the first script. 

chmod 755 ftp.bash will do it. 

As per the naming of it, thats irrelevant, its just good practice to give all your scripts proper extentions. 


let me know what the output is. 

Si

---

### Post by Slim Odds on 2010-01-08
> **Chamillionaire2 said:**
> 
Anyone know why and how to get around this?


Yes, code it properly.... ;)
```
echo Yo!
ftp -n -i <<_EOF_
open ftp.server.com
user user password
put contents.txt
close
bye
[COLOR=Red]_EOF_[/COLOR]
echo Go!
```Your version is sending "echo Go!" to the ftp program.

See this: [http://tldp.org/LDP/abs/html/here-docs.html](http://tldp.org/LDP/abs/html/here-docs.html)

---

### Post by Lars Noodén on 2010-01-08
Depending on the particular ftp client, you can pass the username, password and host in a more simple manner.  If you are uploading just a file or two, then ncftpput might help:

```

# make a connection
ncftp -u *user* -p *password* *ftp.example.com*

# put a file
ncftp -u *user* -p *password* *ftp.example.com* . contents.txt

```

See also yafc

[http://linux.die.net/man/1/ncftp](http://linux.die.net/man/1/ncftp)
[http://linux.die.net/man/1/ncftpput](http://linux.die.net/man/1/ncftpput)

---

