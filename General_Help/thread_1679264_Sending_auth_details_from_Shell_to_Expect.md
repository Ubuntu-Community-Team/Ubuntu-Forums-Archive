---
title: "Sending auth details from Shell to Expect"
date: 2011-01-31
forum: General Help
---

### Post by SuaSwe on 2011-01-31
Hi all,

I'm having some trouble with the authentication side of an Expect script I'm attempting to write.

Basically, I have a shell script that is meant to outline/obtain all variables, including username & pass, then send it to the Expect script. Relevant bits of code in shell script at present:

```

# shell.sh

echo -n "Please provide ubr username: "
read username
echo -n "Please provide ubr password: "
read password

[...]

if [ $var2 ] ; then
        ./expect.exp $device $var2 $username $password
else
        echo "No action required"
fi

```

The if statement itself works fine, e.g. if $var2 is present the .exp script executes, and $device and $var2 are both sent over fine (tested this by inputting my username & password directly into the .exp script, and that allows it to go through).

On the Expect side, script looks like so:

```

                #Opens telnet session to device
                spawn /usr/bin/telnet $device
                expect "name:"
                                send "$username\r"

                expect "assword:"
                                send "$password\r"

```

Unfortunately this gives me an authentication error from the $device. As noted, if I input my auth details manually in the Expect script it works fine, so presumably the issue is with how the info is sent from the shell script? Any ideas, anyone? Much obliged!


***********

Managed to solve this! For any- and everyone's info, syntax is now:

```

# shell.sh

device=`cat file | awk $1`
var2=`cat file | awk $2`

get_authentication()
{
        echo -n "Please provide username: ";
        read username;
        echo -n "Please provide password: ";
        read password;
}

get_authentication;


if [ $var2 ] ; then
        ./expect.exp $device $var2 $username $password
else
        echo "No action required"
fi

```

Had actually already tried this though I had the get_authentication() bit at the top, ahead of the variables - either this made some difference or there was a typo in there that I failed to spot!

---

