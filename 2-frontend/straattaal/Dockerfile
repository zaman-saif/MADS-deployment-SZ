FROM raoulgrouls/torch-python-slim:py3.12-torch2.7.1-arm64-uv0.8.13

WORKDIR /app

COPY backend/*.py /app/
COPY backend/requirements.txt /app/requirements.txt
COPY src/slanggen/*.py /app/src/
COPY artefacts/ /app/artefacts/
COPY frontend/ /app/frontend/
COPY assets/ /app/assets/


COPY dist/*.whl /app/

RUN uv pip install "app/slanggen-0.4-py3-none-any.whl[scrape,frontend]""  --system 

EXPOSE 80

# ENV PATH="/app/.venv/bin:$PATH"

# ENTRYPOINT [ "python", "app.py" ]
# ENTRYPOINT ["python", "-m", "src/main" ]
CMD ["python", "-m", "uvicorn", "app:app", "--host", "0.0.0.0", "--port", "80" ]