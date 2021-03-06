pry-byebug
============

_Fast execution control in Pry_

Adds **step**, **next**, **finish**, and **continue** commands and
**breakpoints** to [Pry][pry] using [byebug][byebug].

To use, invoke pry normally. No need to start your script or app differently.

```ruby
def some_method
  binding.pry          # Execution will stop here.
  puts 'Hello World'   # Run 'step' or 'next' in the console to move here.
end
```

For a complete debugging environment, add
[pry-stack_explorer][pry-stack_explorer] for call-stack frame navigation.


## Execution Commands

**step:** Step execution into the next line or method. Takes an optional numeric
argument to step multiple times.

**next:** Step over to the next line within the same frame. Also takes an
optional numeric argument to step multiple lines.

**finish:** Execute until current stack frame returns.

**continue:** Continue program execution and end the Pry session.


## Breakpoints

You can set and adjust breakpoints directly from a Pry session using the
following commands:

**break:** Set a new breakpoint from a line number in the current file, a file
and line number, or a method. Pass an optional expression to create a
conditional breakpoint. Edit existing breakpoints via various flags.

Examples:

```
break SomeClass#run            Break at the start of `SomeClass#run`.
break Foo#bar if baz?          Break at `Foo#bar` only if `baz?`.
break app/models/user.rb:15    Break at line 15 in user.rb.
break 14                       Break at line 14 in the current file.

break --condition 4 x > 2      Change condition on breakpoint #4 to 'x > 2'.
break --condition 3            Remove the condition on breakpoint #3.

break --delete 5               Delete breakpoint #5.
break --disable-all            Disable all breakpoints.

break                          List all breakpoints. (Same as `breakpoints`)
break --show 2                 Show details about breakpoint #2.
```

Type `break --help` from a Pry session to see all available options.


**breakpoints**: List all defined breakpoints. Pass `-v` or `--verbose` to see
the source code around each breakpoint.


## Caveats

Only supports MRI 2.0.0 or newer.


## Tips

Stepping through code often? Add the following shortcuts to `~/.pryrc`:

```ruby
Pry.commands.alias_command 'c', 'continue'
Pry.commands.alias_command 's', 'step'
Pry.commands.alias_command 'n', 'next'
Pry.commands.alias_command 'f', 'finish'
```

Using Pry with Rails? Check out [Jazz Hands][jazz_hands].


## Contributors

* Gopal Patel (@nixme)
* John Mair (@banister)
* Nicolas Viennot (@nviennot)
* Benjamin R. Haskell (@benizi)
* Joshua Hou (@jshou)
* ...and others who helped with [pry-nav][pry-nav]

Patches and bug reports are welcome. Just send a [pull request][pullrequests] or
file an [issue][issues]. [Project changelog][changelog].

[pry]:                http://pry.github.com
[byebug]:             https://github.com/deivid-rodriguez/byebug
[pry-stack_explorer]: https://github.com/pry/pry-stack_explorer
[jazz_hands]:         https://github.com/nixme/jazz_hands
[pullrequests]:       https://github.com/deivid-rodriguez/pry-byebug/pulls
[issues]:             https://github.com/deivid-rodriguez/pry-byebug/issues
[changelog]:          https://github.com/deivid-rodriguez/pry-byebug/blob/master/CHANGELOG.md
