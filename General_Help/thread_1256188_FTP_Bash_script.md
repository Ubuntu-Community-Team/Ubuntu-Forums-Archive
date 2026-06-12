---
title: "FTP Bash script"
date: 2009-09-02
forum: General Help
---

### Post by Chamillionaire2 on 2009-09-02
What's Up?

OK, So I've been googling around for awhile but cant seem any bash scripts that connect to my ftp server and download a text file for me. Anyone know of a working script?

Thanks Bye.

---

### Post by falconindy on 2009-09-02
wget --ftp-user=USER --ftp-password=PASS [ftp://ftp.mydomain.com/mytextfile.txt](ftp://ftp.mydomain.com/mytextfile.txt)

edit: I suppose if this was something common for you, you could add this to your .bashrc or .bash_aliases (or wherever you keep them)

```
myftpget() {
     wget --ftp-user=USER --ftp-password=PASS [ftp://ftp.mydomain.com/$1]("ftp://ftp.mydomain.com/mytextfile.txt")
}
```And then you'd just need to `myftpget path/to/textfile.txt`. But this means you're storing your ftp password in plain text... you could re-enter it every time like so...

```
myftpget() {
    wget --ftp-user=USER --ftp-password=$1 [ftp://ftp.mydomain.com/$2]("ftp://ftp.mydomain.com/mytextfile.txt")
}
```Which would then be executed as `myftpget password path/to/textfile.txt`.

---

### Post by sedawk on 2009-09-02
The easiest way is to use wget as described above.

For interactive tools like an ftp client you normally need
something like the tool "expect" to use the tool from inside
a script.
There are some ways to send input to interactive tools
like an ftp client from a non-interactive script
(using a here document, or using a sequence of echo+sleep+echo+sleep
in a pipe), but the best solution is to use 'expect'.

But in your case wget (or maybe curl) are the easiest solutions.

---

