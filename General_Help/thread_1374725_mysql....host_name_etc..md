---
title: "mysql....host name etc.????"
date: 2010-01-07
forum: General Help
---

### Post by old_dog on 2010-01-07
Using synaptic package manager installed mysql, using the mysql Adminstrator gui it asks for "stored connection", "port"(with the value 3306) "hostname", "username" and "password". Give me a clue please.....

On the command line anything prefixed with mysql cant be found???
I'm sure the answer is staring me in the face and I'm going to feel incredibly stupid when you tell me the answer
Cheers

---

### Post by Cheesemill on 2010-01-07
If MySQL is on the same machine that your running MySQL Administrator on then:
 
Port = 3306 (This is the default MySQL port)
Host name = localhost
Username = root
Password = password you gave when installing MySQL

---

### Post by old_dog on 2010-01-07
Couldn't find localhost
Just had a thought based on your reply cheesemill.....I changed the localhost in apache does this mean that the "localhost" for mysql is different to for want of a better term to "my localhost"
Cheers old dog

---

### Post by Cheesemill on 2010-01-07
As far as I know the localhost setting in Apache shouldn't affect MySQL.
 
Try using 127.0.0.1 instead of localhost.

---

### Post by old_dog on 2010-01-07
Suitably embarrassed hadn't downloaded the server!!!!
Thanks Cheesemill

---

