---
title: "Setting different file permissions for two distinct groups"
date: 2010-10-28
forum: General Help
---

### Post by natomb on 2010-10-28
Hello,

I am sure this is a very common question but I failed to narrow down my search in e.g. google to find relevant information.

I have the following situation:

- directory "d" should be configured for file permissions
- file permissions of "d" shall be inherited to all contained files and directories
- group "a" shall be permitted to write to "d"
- group "b" shall be permitted to read from "d"
- everyone else shall be denied to access "d"

How can I configure this? Using "chgrp a d" and then "chmod 770 d" would give "a" the proper permission any deny everyone else, but how would I then limit group "b" to read access?

Many thanks for an answer to - I believe - this simple question.

Bjoern

---

### Post by sisco311 on 2010-10-28
You can't do that with the standard Unix/Linux file permissions. You have to use ACLs.

Here is the community documentation: [uhelp]community/UbuntuLTSP/ACLSupport[/uhelp]

I think the YouTube video tutorial is very good: [http://www.youtube.com/watch?v=6piQXXHTmqk](http://www.youtube.com/watch?v=6piQXXHTmqk)

---

### Post by natomb on 2010-10-28
Thank you very much for the hint.

Actually, I discovered this option and configured in the following way:

```

mkdir d
chgrp a d
chmod 770 d
setfacl -m default:group:b:rx

```

It appeared to me that it is important to define the access privileges for group "b" as default for inheritance.

---

