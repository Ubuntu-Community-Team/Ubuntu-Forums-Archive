---
title: "Ldapsearch windows server 2008 AD"
date: 2009-11-17
forum: General Help
---

### Post by jonesg on 2009-11-17
First excuse me if this is the wrong place to post this question but i wasn't entirely sure where to put it.

I'm currently working on a script to help linux users in our Windows Server 2008 AD environment.

This brings be to the problem. I'm creating a script that given a users email will query the correct domain controller for a certain property. I have created this ldapsearch command:

ldapsearch -h do.ma.in -x -D username@do.ma.in -W -b 'DC=do,DC=ma,DC=in' cn=username

Now this command will prompt the user for a password and given this return all properties. This works fine when running it from the command line but as soon as i put it inside a bash script it fails with error code 10 which is a referral error:

Referral (10)
Additional information: 0000202B: RefErr: DSID-031007EF, data 0, 1 access points
        ref 1: 'ma.in''

Referral: ldap://ma.in'/'DC=do,DC=ma,DC=in'

It is running the exact same command and this is why I'm so confused as to why it doesn't work.

My best bet is that something changes when running the command in a bash script as to the environment but i can't seem to see what could affect it in this way.

Does anyone know this problem and perhaps even a solution to this?

---

### Post by Fire_Chief on 2009-11-17
When you run it in the script, do you get prompted for the password? I've had some similarly weird script issues before.

---

### Post by jonesg on 2009-11-18
I get prompted yes but in a strange way. When the script is run on my Ubuntu box it doesn't write the "Please enter LDAP password" text, it just waits for it. The same happens if I strap a "| grep" on i afterwards.

On another machine i tested running RHEL it does write the "please enter password" but the same error occurs.

---

