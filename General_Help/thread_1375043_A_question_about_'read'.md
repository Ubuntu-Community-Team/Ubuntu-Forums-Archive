---
title: "A question about 'read'"
date: 2010-01-07
forum: General Help
---

### Post by BCven86 on 2010-01-07
I am trying to run a short script that will read a line from a file, perform an action on the line, and then ask a user for a response.

i.e.

```

cat randorder.txt | while read line; do
        sleep 2;
        play -q $line; sleep 1;
        echo "What sound did you hear? ";
        read response; echo $response
        echo "$line   :   $response" >> response.txt
done

```

My problem is that the while loop doesn't wait for the second read and even when I do type a response in the field, the "echo $response" seems to echo the value of $line instead. Can someone who knows more about 'read' help me fix this problem?

---

