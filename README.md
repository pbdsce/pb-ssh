Here is the final combined `README.md` that includes:

* What the repo is for
* How keys are managed
* How to SSH into the server
* How to use an alias
* How to contribute keys or revoke them

---

````markdown
# 🔐 Pointblanks SSH Key Management

This repository manages SSH access to the **Pointblanks server** using GitHub Actions. It syncs the `authorized_keys2` file to the server, which is separate from system-level `authorized_keys`. This allows safe, team-managed access that can be rotated or revoked via pull requests.

---

## 🧩 Server SSH Access

Once your key is approved and merged, you can access the server using:

```bash
ssh devopswale@teleport.pointblank.club
````

---

## 📁 Recommended: SSH Config Alias

To simplify repeated SSH access, add the following to your `~/.ssh/config`:

```bash
Host pbserver
  HostName teleport.pointblank.club
  User devopswale
```

Now you can simply run:

```bash
ssh pbserver
```

---

## 📝 Requesting Access

To add your key:

1. **Fork** this repo and create a **new branch**.

2. Open the `authorized_keys2` file.

3. Add your SSH public key below a comment in this format:

   ```bash
   # Name - Why you need it - Until when
   ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIE... yourname@device
   ```

   ✅ **Example:**

   ```bash
   # Govind - Deployment access for server fixes - until 2025-06-30
   ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIBVb9wOe... govind@laptop
   ```

4. **Commit and push** your changes.

5. **Open a pull request** to `main`, and include the same details in the PR description:

   ```
   # Govind - Deployment access for server fixes - until 2025-06-30
   ```

6. Once merged, your key will be deployed automatically by GitHub Actions.

