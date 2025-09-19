# Data Conversion (UiPath)

A small UiPath workflow that asks for a **name** and **age**, calculates the **year of birth**, and shows a message:
```
Hello Sean, You were born in 1995
```

## Features
- Collects a user's name and age using **Input Dialog** activities.
- Converts the age from text to a number.
- Calculates year of birth with the current year.
- Displays the result in a **Message Box**.

## Requirements
- UiPath Studio **2025.0.172 STS** (or newer).
- .NET runtime that comes with UiPath Studio.
- Default **UiPath.System.Activities** package (included by default).

## Getting Started
1. Open **UiPath Studio**.
2. Create a new **Process** project (e.g., `Data Conversion`).
3. Add a **Sequence** named **Sequence – 'Data Conversion'** to `Main.xaml`.
4. Add the activities and variables listed below.
5. Click **Run** to test.

## How It Works (workflow steps)
1. **Input Dialog – User Name**  
   - Title: `Name`  
   - Label: `Enter your Name`  
   - Output (String): `userName`
2. **Input Dialog – User Age**  
   - Title: `Age`  
   - Label: `Enter your Age`  
   - Output (String): `userAgeText`
3. **Assign – Convert Age**  
   - `intUserAge` = convert `userAgeText` to number  
   - VB: `CInt(userAgeText)`  
   - C#: `Int32.Parse(userAgeText)`
4. **Assign – Year of Birth**  
   - `intYearOfBirth` = `Now.Year - intUserAge`
5. **Message Box – User Details**  
   - Text: `"Hello " + userName + ", You were born in " + intYearOfBirth.ToString()`

## Variables
| Name            | Type   | Purpose                            |
|-----------------|--------|------------------------------------|
| `userName`      | String | Stores the user's name             |
| `userAgeText`   | String | Stores the age as text from dialog |
| `intUserAge`    | Int32  | Age converted to a number          |
| `intYearOfBirth`| Int32  | Calculated year of birth           |

## Example
- Input: `Sean`, `30`  
- If the current year is `2025`, the message will be:  
  `Hello Sean, You were born in 1995`

## Troubleshooting
- **Type conversion error** (String → Int32): make sure you convert `userAgeText` using `CInt(...)` (VB) or `Int32.Parse(...)` (C#) before calculating the year.
- **Activities not found**: in the **Activities** panel, enable **Show Classic** or confirm the **UiPath.System.Activities** package is available.
- **Empty Message Box**: check that the **Text** property uses the full expression shown above.

## Notes
- The workflow works in both VB and C# projects. Use the matching expression for your project language.
- For invalid input (e.g., letters in age), consider wrapping the conversion in a **Try Catch** and showing a friendly error.

## License
MIT. You can change this to any license you prefer.
