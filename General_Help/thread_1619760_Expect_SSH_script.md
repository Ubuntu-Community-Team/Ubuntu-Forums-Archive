---
title: "Expect SSH script"
date: 2010-11-12
forum: General Help
---

### Post by btindie on 2010-11-12
I've got an Expect script that establishes a ssh connection to the iLO interface of a server. Problem is it drops me back to the local terminal and I can't enter commands to be executed on the remote host. How do I get it so it logs me into the server then leaves me connected to it?

```
expect -f - <<-expect_script_end
        spawn ssh -o StrictHostKeyChecking=no $user@$host
        match_max 100000
        expect "*?assword:*"
        send -- "$pass\r"
        send -- "\r"
        expect eof
expect_script_end
```

Edit: The ssh server running on the iLO interface appears to be sending eof's which is causing expect to exit. How can I get it to ignore them?

---

### Post by TSJason on 2010-11-12
Try using "interact" before your last send.

---

### Post by btindie on 2010-11-12
I tried that but for some reason it bails out on an EOF. It seems that all responses from SSH on the iLO interface include an EOF at the end. Is there a way to ignore the EOF and not terminate?

---

### Post by TSJason on 2010-11-12
So you're saying that the same script works on a standard linux machine, but on iLO it dies before allowing interaction?

For reference I use a similar script for some autoconnect features and it looks like this:


```
expect -c "
                set timeout $expecttimeout
                spawn -noecho ssh -q -oStrictHostKeyChecking=no -oCheckHostIP=no $username@$destserver $sendstring
                trap {
                        set rows [stty -a |head -1 |awk -Frows '{print $2}'|awk -F\; '{print $1}']
                        set cols [stty -a |head -1 |awk -Fcolumsn '{print $2}'|awk -F\; '{print $1}']
                        stty rows $rows cols $cols
                } WINCH
                        stty -echo
                        expect {
                                assword: {
                                        exp_send $password\r
                                        stty echo
                                        interact
                                }  $ {
                                        stty echo
                                        interact
                                }
                        }
        exit"

```

It's inside a larger bash script, hence the extraneous variables.

---

