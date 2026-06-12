---
title: "xinetd imap install"
date: 2011-01-23
forum: General Help
---

### Post by xjx424 on 2011-01-23
Hi,
I'm trying to set up imap on xinetd but am having problems.  
I'm using Ubuntu 8.04

After downloading files I am running "make ldb".  Wasn't sure if I should use ldb or slx or anything else but they all gave me the same results.  They gave me a lot of error messages seen below
```

osdep.c:89:31: error: security/pam_appl.h: No such file or directory
osdep.c:106: warning: âstruct pam_responseâ declared inside parameter list
osdep.c:106: warning: its scope is only this definition or declaration, which is probably not what you want
osdep.c:106: warning: âstruct pam_messageâ declared inside parameter list
osdep.c: In function âcheckpw_convâ:
osdep.c:110: error: invalid application of âsizeofâ to incomplete type âstruct pam_responseâ
osdep.c:111: error: dereferencing pointer to incomplete type
osdep.c:112: error: âPAM_PROMPT_ECHO_ONâ undeclared (first use in this function)
osdep.c:112: error: (Each undeclared identifier is reported only once
osdep.c:112: error: for each function it appears in.)
osdep.c:113: error: invalid use of undefined type âstruct pam_responseâ
osdep.c:113: error: dereferencing pointer to incomplete type
osdep.c:113: error: âPAM_SUCCESSâ undeclared (first use in this function)
osdep.c:114: error: invalid use of undefined type âstruct pam_responseâ
osdep.c:114: error: dereferencing pointer to incomplete type
osdep.c:116: error: âPAM_PROMPT_ECHO_OFFâ undeclared (first use in this function)
osdep.c:117: error: invalid use of undefined type âstruct pam_responseâ
osdep.c:117: error: dereferencing pointer to incomplete type
osdep.c:118: error: invalid use of undefined type âstruct pam_responseâ
osdep.c:118: error: dereferencing pointer to incomplete type
osdep.c:120: error: âPAM_TEXT_INFOâ undeclared (first use in this function)
osdep.c:121: error: âPAM_ERROR_MSGâ undeclared (first use in this function)
osdep.c:122: error: invalid use of undefined type âstruct pam_responseâ
osdep.c:122: error: dereferencing pointer to incomplete type
osdep.c:123: error: invalid use of undefined type âstruct pam_responseâ
osdep.c:123: error: dereferencing pointer to incomplete type
osdep.c:127: error: âPAM_CONV_ERRâ undeclared (first use in this function)
osdep.c: At top level:
osdep.c:138: error: expected â)â before â*â token
osdep.c: In function âcheckpwâ:
osdep.c:155: error: âpam_handle_tâ undeclared (first use in this function)
osdep.c:155: error: âhdlâ undeclared (first use in this function)
osdep.c:156: error: storage size of âconvâ isnât known
osdep.c:164: error: âPAM_SUCCESSâ undeclared (first use in this function)
osdep.c:165: error: âPAM_RHOSTâ undeclared (first use in this function)
osdep.c:168: error: âPAM_ESTABLISH_CREDâ undeclared (first use in this function)
osdep.c:184: error: âcheckpw_cleanupâ undeclared (first use in this function)


```After that it creates most of the new files needed but not all.  
Any ideas what is wrong here?

---

