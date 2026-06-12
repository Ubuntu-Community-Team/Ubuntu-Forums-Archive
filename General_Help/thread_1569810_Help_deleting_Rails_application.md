---
title: "Help deleting Rails application"
date: 2010-09-07
forum: General Help
---

### Post by superbryan on 2010-09-07
Hi all,

I'm new to the forums, and to linux, so I hope this is the best place to post this question.

I want to know if anyone knows how to remove an app (or in this case, a test/learning app) from Rails 3?

I could just delete the folder, but I'm worried it will leave annoying residual files around that I will never find (database, server, configurations, etc...).

Especially since I'm new to linux, I don't even know how to be aware of what files may have been generated/changed as a result of making a new rails app.

Thank you!

(Running Ubuntu 10.04, if it applies)

---

### Post by superbryan on 2010-09-09
50 views and no answers?

---

### Post by stevebu56 on 2010-09-09
If you used the rails command line to create the app like so 
```
rails new my_new_rails_app 
```
I believe it will print out a list of files that it created.  If it doesn't do that by default look for a verbose option.  But most likely deleting the directory will eliminate everthing.

---

