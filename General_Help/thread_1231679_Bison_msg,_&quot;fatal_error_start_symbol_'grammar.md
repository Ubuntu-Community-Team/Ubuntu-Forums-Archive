---
title: "Bison msg, &quot;fatal error: start symbol 'grammar' does not derive any sentence"
date: 2009-08-04
forum: General Help
---

### Post by Garvey on 2009-08-04
The attached parse.doc is actually a parse.y but for loading purposes I had to rename it.

When I run
Bison now, then the messages I get from that are...
parse.y: warning: 8 useless nonterminals and 30 useless rules
parse.y:52.1-7: fatal error: start symbol grammar does not derive any
sentence

I believe that The particular code it refers to is...
%%
grammar:  domains
          constants
          predicates
        ;

My intention is that it reads a set of domains...
typically each one is to a line of a format...
D0 11 0 10  // domainName, number_of_values, floor_value, ceil_value
...
Then reads a set of constants...
typically each one to a line of a format...
X0 D0 9

Then reads and processes a set of predicates, each one to a line, which
may appear as...
or(lt(mul(X0,X1),X2),ge(abs(sub(X3,X4)),X5))

However,  I have no precedent or pro-forma for such as 'grammar' above.  I
think that the domains constants predicates sequence I've written will
read all the
domains, then all the constants then all the predicates without allowing
any regression through any of them (eg a domain in the constants).

That the start symbol 'grammar' cannot derive any sentence only suggests
to me that the grammar high level nonTerminal cannot access it's
subsidiary terminals and non-terminals, but the exact cause is not yet
clear to me.

The classic example such as p75  of lex & yacc...[1995 Levine et al]
statement_list: statement '\n'
       statement_list  statement '\n'
    ;
...doesn't shed much light on my codes attached below, where I must read a
group of domains, followed by a group of constants, followed by a group of
predicates.

---

