---
title: "field 'struct' has incomplete type"
date: 2011-05-13
forum: General Help
---

### Post by deceaseddolphin on 2011-05-13
Hi,

I'm building a symbol table and syntax tree using lex and yacc for a compiler.

I am stuck with an error for too long. I have defined two structures (one for Symbol Table and another for Syntax Tree).

```

typedef struct symbolTable{
char name[30];
.....
struct symbolTable *next;
}*symtable;

typedef struct treeNode{
nodekind kind;
....
}*SyntaxTree;

typedef struct treeNode node;

```then I have defined the types of nodes in union as

```

%union{
struct treeNode *stnode;
struct symbolTable info; // <= error pointed here
};

```here's the error:

**bottomup.y:76: error: field 'info' has incomplete type.**

I tried to define the structure definitions in a separate header file and included in .y file but it didn't work out.

I'm trying to get this done ASAP.

Any help will be appreciated!

Thanks.

P.S: Please note that the union definition is made in yacc file.

---

### Post by deceaseddolphin on 2011-05-15
I changed the structure of both the structures.

I messed up using one for another.

This is SOLVED!

---

