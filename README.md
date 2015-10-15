# Ruby wats

A "wat" is what I call a snippet of code that demonstrates a counterintuitive edge case of a programming language. The name comes from [pywat](https://github.com/cosmologicon/pywat) and [this excellent talk by Gary Bernhardt](https://www.destroyallsoftware.com/talks/wat). If you're not familiar with the language, you might conclude that it's poorly designed when you see a wat. Often, more context about the language design will make the wat seem reasonable, or at least justified.

## The wats

### Undefined variables and assignment

    > a
    => NameError: undefined local variable or method `a` for main:Object
    > b
    => NameError: undefined local variable or method `b` for main:Object
    > a = b
    => NameError: undefined local variable or method `b` for main:Object
    > a = a
    => nil # WAT?

Another one.

    > c = 1 if c == 1
    => nil # WAT? No error?
    > c => nil # Wat?

And my personal favorite:

    > a = a.nil?
    => true

### Division by Zero

    0 / 0
    => ZeroDivisionError: divided by 0
    0.0 / 0
    => NaN

### Hash assignement

    > my_hash = Hash.new []
    => {}
    > my_hash[:hobbies] << 'dancing';
    > my_hash[:hobbies] << 'swimming';
    > my_hash[:skills]  << 'java';
    > my_hash[:skills]  << 'php';
    > my_hash[:skills]
    => ["dancing", "swimming", "java", "php"]
    > my_hash[:some_random_key]
    => ["dancing", "swimming", "java", "php"]
