---
title: "some help explaining the shadow file"
date: 2012-03-11
forum: General Help
---

### Post by nickda_corfu on 2012-03-11
i have been reading loads of articles that 'explain' the format of the shadow password file. However this still does not seem to have cleared it up for me. 
Ill give the following example from an entry of a shadow file :
TestUser1:$1$Le1zSji2$sxt0bp0v1RHlVcXaSkmSi/:15072:0:994599:2:::

Obviously the first part is the username (TestUser1)
I also seem to understand that the $1$ means its an MD5 hash.
Now according to what i have been reading the next part (Le1zSji2$sxt0bp0v1RHlVcXaSkmSi/) should be an MD5 hash however there are 2 problems with this, firstly the $ and / symbol are not valid MD characters and also the length is wrong (should be 32 characters ). 
 I know i am missing something here, could someone please explain it to me? 
 Thanks

---

### Post by sisco311 on 2012-03-11
From **man 3 crypt**:
```
NOTES
   Glibc Notes
       The glibc2 version of  this  function  supports  additional  encryption
       algorithms.

       If  salt is a character string starting with the characters "$id$" fol&#8208;
       lowed by a string terminated by "$":

              $id$salt$encrypted

       then instead of using the DES machine,  id  identifies  the  encryption
       method  used  and  this  then  determines  how the rest of the password
       string is interpreted.  The following values of id are supported:

              ID  | Method
              &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
              1   | MD5
              2a  | Blowfish (not in mainline glibc; added in some
                  | Linux distributions)
              5   | SHA-256 (since glibc 2.7)
              6   | SHA-512 (since glibc 2.7)

       So   $5$salt$encrypted   is   an   SHA-256   encoded    password    and
       $6$salt$encrypted is an SHA-512 encoded one.

       "salt" stands for the up to 16 characters following "$id$" in the salt.
       The encrypted part of the password string is the actual computed  pass&#8208;
       word.  The size of this string is fixed:

       MD5     | 22 characters
       SHA-256 | 43 characters
       SHA-512 | 86 characters

       The  characters  in  "salt"  and  "encrypted"  are  drawn  from the set
       [a&#8211;zA&#8211;Z0&#8211;9./].  In the MD5 and SHA implementations the  entire  key  is
       significant (instead of only the first 8 bytes in DES).

```

Also check out **man 5 shadow**.


*Le1zSji2* is the salt and *sxt0bp0v1RHlVcXaSkmSi/* is the computed password.


HTH

---

### Post by nickda_corfu on 2012-03-11
that clears up quite a bit of confusion i had. thanks a lot

---

