# Control Flow Constructs

In Rust, control flow is managed through various structures like `if`, `else`, `while`, `for`, `loop`, `match` and so-called "labels".

1. The `if` and `else` structures are used to execute different blocks of code based on certain conditions.
2. Similar to other languages, `while` and `for` are used for looping over a block of code.  
2.1. The `while` loop repeats a block of code until the condition is false.  
2.2. The `for` loop is used to iterate over a collection of values like an array or a range.  
2.3. The `loop` is a bit unusual/unexpected feature of Rust that sets it apart from other languages.  
   Which, though, is pretty much simple by definition: it's just an **infinite loop**.
   It works pretty much the same as other types of loops, but there is a single quirk that makes it different: **it can actually return a value** and is treated as an expression block.
   ```rust
   fn main() {
       let counter = 0;
       let my_var = loop {
           if counter > 9 {
               break counter + 1;
           }
           counter += 1;
       };
       println!("Counter is : {}. The my_var is : {}", counter, my_var);
   }
   ```
   Which gives `Counter is : 10. The my_var is : 11`
4. The `match` structure is a powerful tool in Rust which can be used for pattern matching.  
   It goes through different cases and executes the block where the match is found.  
   As expected the **pattern destructuring** is in work here as well!
   ```rust
   let some_var: Result<Option<i32>, ()> = Ok(Some(3));

   match some_var {
       Ok(Some(x)) => println!("All is ok. There is a value: {}", x),
       Ok(None) => println!("All is alright, but no value has been found"),
       Err(value) => println!("There's an error, and the error is a Unit tuple: {}", value),
   }
   ```
