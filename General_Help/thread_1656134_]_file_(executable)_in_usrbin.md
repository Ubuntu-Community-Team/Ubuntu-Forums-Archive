---
title: "] file (executable) in /usr/bin"
date: 2010-12-30
forum: General Help
---

### Post by yaye on 2010-12-30
Hello,

I'm using 10.04 64-bit and found an executable file "named" ] in /usr/bin .  Does anyone know what this file does, and if it is even supposed to be there?  I've found this file on two different installations of Ubuntu 64-bit.  Thanks.

---

### Post by Nytram on 2010-12-30
Hi, I've got the file [ in the same folder, on Ubuntu and Arch, so I guess it's supposed to be there. What it's for though, I've no idea.

---

### Post by WorMzy on 2010-12-30
It's part of core utils, it's used in shell commands quite a lot.

```
[: [ arg... ]
    Evaluate conditional expression.
    
    This is a synonym for the "test" builtin, but the last argument must
    be a literal `]', to match the opening `['.
[[ ... ]]: [[ expression ]]
    Execute conditional command.
    
    Returns a status of 0 or 1 depending on the evaluation of the conditional
    expression EXPRESSION.  Expressions are composed of the same primaries used
    by the `test' builtin, and may be combined using the following operators:
    
      ( EXPRESSION )	Returns the value of EXPRESSION
      ! EXPRESSION		True if EXPRESSION is false; else false
      EXPR1 && EXPR2	True if both EXPR1 and EXPR2 are true; else false
      EXPR1 || EXPR2	True if either EXPR1 or EXPR2 is true; else false
    
    When the `==' and `!=' operators are used, the string to the right of
    the operator is used as a pattern and pattern matching is performed.
    When the `=~' operator is used, the string to the right of the operator
    is matched as a regular expression.
    
    The && and || operators do not evaluate EXPR2 if EXPR1 is sufficient to
    determine the expression's value.
    
    Exit Status:
    0 or 1 depending on value of EXPRESSION.
```

You don't need to worry about it.

---

### Post by yaye on 2010-12-30
> **Nytram said:**
> Hi, I've got the file [ in the same folder, on Ubuntu and Arch, so I guess it's supposed to be there. What it's for though, I've no idea.

Thanks for the reply.  You are correct, the file is named [ .  I typed the wrong bracket key.  Well, it's good to see I'm not alone.  At first I thought a may have come from a security breech.  Hopefully, someone who knows what it is for will reply.

---

### Post by yaye on 2010-12-30
> **WorMzy said:**
> It's part of core utils, it's used in shell commands quite a lot.

```
[: [ arg... ]
    Evaluate conditional expression.
    
    This is a synonym for the "test" builtin, but the last argument must
    be a literal `]', to match the opening `['.
[[ ... ]]: [[ expression ]]
    Execute conditional command.
    
    Returns a status of 0 or 1 depending on the evaluation of the conditional
    expression EXPRESSION.  Expressions are composed of the same primaries used
    by the `test' builtin, and may be combined using the following operators:
    
      ( EXPRESSION )	Returns the value of EXPRESSION
      ! EXPRESSION		True if EXPRESSION is false; else false
      EXPR1 && EXPR2	True if both EXPR1 and EXPR2 are true; else false
      EXPR1 || EXPR2	True if either EXPR1 or EXPR2 is true; else false
    
    When the `==' and `!=' operators are used, the string to the right of
    the operator is used as a pattern and pattern matching is performed.
    When the `=~' operator is used, the string to the right of the operator
    is matched as a regular expression.
    
    The && and || operators do not evaluate EXPR2 if EXPR1 is sufficient to
    determine the expression's value.
    
    Exit Status:
    0 or 1 depending on value of EXPRESSION.
```

You don't need to worry about it.

I guess you responded while I was typing (I'm a very slow typist).  Thanks for the information.

---

