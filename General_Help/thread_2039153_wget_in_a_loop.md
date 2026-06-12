---
title: "wget in a loop?"
date: 2012-08-08
forum: General Help
---

### Post by ryanyeah on 2012-08-08
So I am looking to test my connection by constantly utilising bandwidth. I was looking to somehow loop a wget of a large file, and automatically delete it and redownload it until I wish to stop. Any ideas on how I would go about this?

---

### Post by Zvlwab on 2012-08-08
```

#!/bin/bash
while :
do
    echo "Downloading..."
    wget http://example.com
done

```

---

