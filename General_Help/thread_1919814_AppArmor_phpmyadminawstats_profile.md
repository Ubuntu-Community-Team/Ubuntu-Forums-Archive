---
title: "AppArmor phpmyadmin/awstats profile"
date: 2012-02-03
forum: General Help
---

### Post by Ateo on 2012-02-03
Aloha forum,

I googled until fingertips bled but I wasn't really able to find AppArmor profiles for phpmyadmin nor awstats. So, I'm here to ask if anyone can post their examples OR...... link me as I just wasn't successful.

Thanks.

---

### Post by Dave_L on 2012-02-03
phpmyadmin is still a PHP script, isn't it?  Is it possible for AppArmor to limit a specific PHP script? Or would AppArmor's control only apply to the process that's executing the script, either PHP or, in this case, probably Apache.

---

### Post by Dangertux on 2012-02-03
> **Dave_L said:**
> phpmyadmin is still a PHP script, isn't it?  Is it possible for AppArmor to limit a specific PHP script? Or would AppArmor's control only apply to the process that's executing the script, either PHP or, in this case, probably Apache.

That is correct. It would limit the process executing/interpreting the script.

---

### Post by Ateo on 2012-02-03
makes sense. thanks for responding. i guess the same would apply to awstats... both executed by an apache process...

thanks dudes.

---

