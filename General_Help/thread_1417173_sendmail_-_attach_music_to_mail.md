---
title: "sendmail - attach music to mail"
date: 2010-02-27
forum: General Help
---

### Post by d3v1150m471c on 2010-02-27
How do I use the "mail" command or some other variant to send an attachment other than a text file. Like say I wanted to send an mp3 or a tar.gz file?

Update:
```

#!/bin/bash
###

      (
       cat body.txt
       uuencode song.mp3
      ) |
      mail -s "subject" toemail@email.com

```

---

