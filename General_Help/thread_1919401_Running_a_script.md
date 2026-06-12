---
title: "Running a script"
date: 2012-02-02
forum: General Help
---

### Post by SwaroopKunduru on 2012-02-02
When I am running a bash script of Axis2 at terminal I see a message "You must set the JAVA_HOME variable before running Axis2 Script."

I have exported JAVA_HOME in my .bashrc file when I echo $JAVA_HOME I see "/usr/lib/jvm/java-6-sun"

Could any one help me run the script in Ubuntu11.10


Thanks in advance.

Regards,

Swaroop Kunduru.

---

### Post by lisati on 2012-02-02
*Thread moved to **General Help**.*

---

### Post by galvatron408 on 2012-02-02
you said that this is a bash script right?

type...

bash -x yourscript.sh

now, what does JAVA_HOME equal to?

> **SwaroopKunduru said:**
> When I am running a bash script of Axis2 at terminal I see a message "You must set the JAVA_HOME variable before running Axis2 Script."

I have exported JAVA_HOME in my .bashrc file when I echo $JAVA_HOME I see "/usr/lib/jvm/java-6-sun"

Could any one help me run the script in Ubuntu11.10


Thanks in advance.

Regards,

Swaroop Kunduru.

---

