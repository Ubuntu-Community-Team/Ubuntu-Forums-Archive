---
title: "output one email at a time"
date: 2010-04-30
forum: General Help
---

### Post by jeff.sadowski on 2010-04-30
I would like a way to output one email at a time on the command line so that I could use scripting to process some of my emails. Here is my crude attempt at doing said task. I would like some suggestions of better programs to do this.


# This Function has know bugs of the possibility of emails getting
# removed without proccessing due to the chance of an email comming
# after catting /var/spool/mail/${USER} and before the clearing of it.
#
# This function pulls all mail from /var/spool/mail/${USER} and puts
# it in a file ${HOME}/.onemail working with it in a way that as long
# as one instance of it is running it insures that one mail is
# processed at a time.
#
# I'm sure there are better ways to do this and garentee better results
# but I could not find a commandline mail reader that would just display
# the next unread message.
onemail(){
cat /var/spool/mail/${USER} >> ${HOME}/.onemail
echo -n >  /var/spool/mail/${USER}
Next=`grep -n "^From " ${HOME}/.onemail|head -n 2|tail -n 1|cut -d: -f1`
if [ "${Next}" = "" ];then Next=0;fi
if [ "${Next}" -lt "3" ]; then
cat ${HOME}/.onemail;echo -n > ${HOME}/.onemail
else
let Next=${Next}-2
Lines=`wc -l .onemail| cut -d" " -f1`
let Left=${Lines}-${Next}
head -n $Next ${HOME}/.onemail
tail -n $Left ${HOME}/.onemail > ${HOME}/.onemail.tmp
cat ${HOME}/.onemail.tmp > ${HOME}/.onemail
rm -rf ${HOME}/.onemail.tmp
fi
}


-----------------------------------------------------------


after playing with mail a while I figured a much better solution

onemail(){ echo 1|mail;}

but I still have an issue that is is being deleted. For what I am using it for this works though.

---

