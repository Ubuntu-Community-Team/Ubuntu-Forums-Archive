---
title: "help sed: substitution switch"
date: 2009-10-29
forum: General Help
---

### Post by pankajphartiyal on 2009-10-29
pankaj@ubuntu:~/linux$ sed '1,3s/|/:/g' emp.lst

1245:dasgupta, S. N.        :manager        :sales        :7600
1114:aggrawal, anil        :manager        :sales        :8500
5684:chakrobarty, sumit        :deputy general manager    :marketing    :7000
5541|chowdury, lalit        |director        |marketing    |8000
6612|saxena, J. B.        |general manager    |marketing    |6140
[COLOR=DarkOrange]
[B]this is working fine
but if i do reverse, it fails[/B][/COLOR] 

pankaj@ubuntu:~/linux$ sed '1,$s/|/:/g' emp.lst

1245:dasgupta, S. N.        :manager        :sales        :7600
1114:aggrawal, anil        :manager        :sales        :8500
5684:chakrobarty, sumit        :deputy general manager    :marketing    :7000
5541:chowdury, lalit        :director        :marketing    :8000
6612:saxena, J. B.        :general manager    :marketing    :6140


pankaj@ubuntu:~/linux$ sed '1,3s/:/|/g' emp.lst

1245|dasgupta, S. N.        |manager        |sales        |7600
1114|aggrawal, anil        |manager        |sales        |8500
5684|chakrobarty, sumit        |deputy general manager    |marketing    |7000
5541|chowdury, lalit        |director        |marketing    |8000
6612|saxena, J. B.        |general manager    |marketing    |6140

---

### Post by DaithiF on 2009-10-29
Hi,
You know that your sed commands aren't actually changing the file emp.lst though, right?  The results you see from the 1st and 2nd commands are just being output to the stdout, the input file itself is not being changed.  So I don't think the 'reverse' sed command is failing, its just that there is no data to match the pattern because the file is still the same as it was at the beginning.

So use the -i flag with sed to change the file in-place.

---

