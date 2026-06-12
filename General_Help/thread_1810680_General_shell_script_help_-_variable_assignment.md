---
title: "General shell script help - variable assignment"
date: 2011-07-23
forum: General Help
---

### Post by OBI_Ron on 2011-07-23
Hello Everyone,

I am up and running in Amazons EC2, and I have installed and configured the ec2 scripting tools.

The following command extracts the Public DNS from the indicated running instance:

ec2-describe-instances i-XXXXXXXX |grep INSTANCE|cut -f4

Results:

ec2-XX-XX-XXX-XXX.compute-1.amazonaws.com

I would like to assign this result to a variable, however, all my attemps result in the following error regardless of how I use quotes:

PDNS=ec2-describe-instances i-XXXXXXXX |grep INSTANCE|cut -f4

Results:

i-XXXXXXXX: command not found

Is there a default $Variable that gets set with the results of the last command?  If not, how can I set the results of the command mentioned above to a variable?

Thanks in advance!

---

### Post by OBI_Ron on 2011-07-23
Got it!

I needed to use the `(lower case ~(tilde)).The following line worked:

PDNS=`ec2-describe-instances i-XXXXXXXX |grep INSTANCE|cut -f4`

echo $PDNS
ec2-XXX-XX-XXX-XXX.compute-1.amazonaws.com

If you are going to use it to connect via ssh, you mihgt set it as follows:
PDNS=user@`ec2-describe-instances i-XXXXXXXX |grep INSTANCE|cut -f4`

---

