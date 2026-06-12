---
title: "User startup script"
date: 2010-02-25
forum: General Help
---

### Post by kefivx on 2010-02-25
Hello everyone;

I'm new to these forums.  And before we go too far, I feel that I should mention that I am not an Ubuntu user.

I've asked my question on a few other forums, but have gotten no responses.

Perhaps one of you can help. :)

What I need is for an application to get run when a specific user logs on.  For example, if user1 logs on, the application is run; but if user2 logs in, the application is not.  More specifically, when user1 (and only user1) logs on, I want to start X.

Anyone have an idea?  Thanks in advance.

---

### Post by kefivx on 2010-02-25
bump

---

### Post by kefivx on 2010-02-25
Anyone?

---

### Post by kefivx on 2010-02-25
Just in case someone else runs into this problem,

~/.bash_login is the answer.  How I solved it:
```

vim ~/.bash_login

#!/bin/sh
./script_to_execute.sh

```

And the problem is solved.

---

