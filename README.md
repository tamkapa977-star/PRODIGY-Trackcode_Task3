import string

def check_password_strength(password):
    score = 0
    feedback = []

    # Length check
    if len(password) >= 8:
        score += 1
    else:
        feedback.append("Password should be at least 8 characters long.")

    # Uppercase check
    if any(char.isupper() for char in password):
        score += 1
    else:
        feedback.append("Add at least one uppercase letter.")

    # Lowercase check
    if any(char.islower() for char in password):
        score += 1
    else:
        feedback.append("Add at least one lowercase letter.")

    # Number check
    if any(char.isdigit() for char in password):
        score += 1
    else:
        feedback.append("Add at least one number.")

    # Special character check
    special_chars = string.punctuation
    if any(char in special_chars for char in password):
        score += 1
    else:
        feedback.append("Add at least one special character (!, @, #, etc.).")

    # Strength level
    if score == 5:
        strength = "🔥 Strong Password"
    elif score >= 3:
        strength = "⚠️ Medium Password"
    else:
        strength = "❌ Weak Password"

    return strength, feedback


def main():
    print("=== Password Strength Checker ===")

    password = input("Enter your password: ")

    strength, feedback = check_password_strength(password)

    print("\nResult:", strength)

    if feedback:
        print("\nSuggestions:")
        for item in feedback:
            print("-", item)


if __name__ == "__main__":
    main()
