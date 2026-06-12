---
title: "qstat output"
date: 2010-04-09
forum: General Help
---

### Post by garfieldpbj on 2010-04-09
Hi.

Can anyone explain to me why qstat gives "..." + the last 12 characters of the job name; whereas qstat -n -1 gives the first 10 characters of the job name? 

I would like to see which and how many nodes the jobs are running at + the last part of the filename (or even better I want the following: jobID, username, full job name, elapsed time and used nodes) 

Do anybody know how to do this?

/Peter

---

### Post by Claus7 on 2010-04-09
Hello,

a quick thing for you to try would be:
```
qstat -f
```

Regards!

---

### Post by garfieldpbj on 2010-04-09
> **Claus7 said:**
> Hello,

a quick thing for you to try would be:
```
qstat -f
```

Regards!

Hi..

Thank you for your suggestion..

I know that, but then I get a lot information, which I do not want..

And I am not able to "grep out" what I want and put it in one line per job.

/Peter

---

### Post by Claus7 on 2010-04-10
Hello, 

then I would try something like:

```
qstat -g t -u *name_of_user*

or

qstat -j *#of_job_id* | grep -e "hard_queue_list" -e "uid" -e "submission_time"
```

The problem with the first one is that it shows all the slots a job takes so if it is parallel you will get a lot of output.

For the second one you have not only to specify the job id you want to see more info, but also that specific info you want to get for that job, by executing multiple greps.

I noticed that some of the options you specify (e.g. the -n option) do not work in my environment, so experimenting with yours might be the best solution.

Maybe someone else can provide more info.

Regards!

---

### Post by garfieldpbj on 2010-04-13
> **Claus7 said:**
> Hello, 

then I would try something like:

```
qstat -g t -u *name_of_user*

or

qstat -j *#of_job_id* | grep -e "hard_queue_list" -e "uid" -e "submission_time"
```


None of the g, t or j parameters work - the reason might be that the server which I am communicating with is running CentOS, which I first realized recently.. 

I would still like suggestions :-) 

/Peter

---

### Post by Claus7 on 2010-04-13
Hello,

> **garfieldpbj said:**
> None of the g, t or j parameters work - the reason might be that the server which I am communicating with is running CentOS, which I first realized recently.. 

I would still like suggestions :-) 

/Peter

there is no possibility, probability or whatever these commands not to work. Did you have any job at the time running, when you tested them? Which version of Centos are you using (cat /etc/redhat-release)?

Can you see if by typing:
man qstat
that these options are valid? 

You should know exactly what you are typing cause if not so, most of the time the commands you type will create no results.

Just these simple thought at the moment.

EDIT: I think that in the above commands you discern that *name_of_user* is your user name, so you have to switch that with yours and the #of_job_id is the id number of a job that is running. So first of you have to see your jobs id that are running, and then for each one to see the specific informations you want.

Regards!

---

