// csci_6221 Advanced Software Paradigms The project stems from Master level coursework at George Washington University's SEAS.
//#Safer-Systems-Programming is a two- part project to evaluate Rust as an uncommonly used programming language. In part (a), I evaluate Rust using //explicitly required criteria and consider cybersecurity as independent criteria. 
//For part (b), I implment a guessing game which I found in "The Book" https://doc.rust-lang.org/book/
//filename:  src/main.rs
use std::io;
use rand::Rng;
use std::cmp::Ordering;

fn main(){
    println!("Guess the number!");   
    let secret_number = rand::thread_rng().gen_range(1..101);
   // let mut guess = String::new();
   // println!("The secret number is: {}", secret_number);
    
    loop{
        println!("Please input your guesss.");
        let mut guess = String::new();
        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line");
        let guess:  u32 = guess.trim().parse().expect("Please type a number!");
       
        println!("You guessed: {}", guess);   
        match guess.cmp(&secret_number){
            Ordering::Less => println!("Too small!"),
            Ordering::Greater => println!("Too big!"),
            Ordering::Equal => println!("You win!"),
        }
    }
}
